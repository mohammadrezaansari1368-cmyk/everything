# npm supply-chain scanning

> Guidance transcribed from the comments in `.github/workflows/npmscan.yml` at `b38be6a7f6350964d59328b52f0624e1d1d552d1` in [https://github.com/affaan-m/ECC](https://github.com/affaan-m/ECC). The workflow, the third-party action, and the scanner scripts were not copied. Nothing in this folder uploads dependency files or contacts a scanning host.

## What the upstream check is for

When `package.json`, `package-lock.json`, or `yarn.lock` changes on a pull request, upstream ECC runs a warn-only dependency check. It compares the base and pull-request versions of those files and reports:

- known malware or vulnerabilities in changed packages
- new install scripts
- swapped tarballs or checksums
- dependency override changes

The check is warning-only. It comments when it finds something. It is not, by itself, a failing merge gate. The fuller report is written to the job summary.

The job refuses to scan a dependency path that is a symlink or not a regular file.

## What the upstream description says about data

- Environment variables and the GitHub token are not intentionally included.
- Values already stored inside the dependency files are part of the input. That includes registry URLs and the `scripts` fields.
- Checkout credentials are not persisted.
- The third-party action is pinned to a commit SHA.

## What this copy does not do

This repository does not include:

- `.github/workflows/npmscan.yml`
- `.github/workflows/supply-chain-watch.yml`
- `scripts/ci/scan-supply-chain-iocs.js`
- `scripts/ci/supply-chain-advisory-sources.js`
- any instruction to send lockfiles to npmscan.com or any other host
- any instruction to install or execute a scanner

Read the upstream workflow if a maintainer wants the live check. Do not re-add it here, and do not ask an agent to upload dependency manifests.

## Companion policy

From upstream `SECURITY.md`, kept as policy only:

- Pin third-party GitHub Actions to commit SHAs.
- Do not interpolate untrusted GitHub event context into workflow shell steps.
- Point release and install documentation only at packages the project lists as official.
- Keep private vulnerability reports private until disclosure is coordinated.

The incident playbook, with scanner and install commands removed, is [supply-chain-incident-response.md](supply-chain-incident-response.md).
