# Engineering Guide

## General Principles

- Prefer small, cohesive, well-tested changes over sweeping rewrites.
- Keep public interfaces explicit, typed, and validate all external inputs at I/O boundaries.
- Never commit secrets, tokens, or environment-specific credentials.
- Document breaking changes clearly in commit messages and pull requests.
