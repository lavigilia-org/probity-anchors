# Probity anchors

Daily public timestamps of the working repositories of La Vigilia, an association in formation in Rome.

La Vigilia commits to making the way its work is built verifiable by third parties. This repository is the first public layer of that commitment, ahead of its integrity platform, Probity.

## What is published

Once a day, around 23:00 Rome time, one file in `heads/<year>/` records the identifier of the latest commit on the main branch of each working repository, under a stable label:

- `steering`: decisions, register and governance;
- `doctrine`: the doctrine, what the project is and what it forbids itself;
- `situations`: the situation generator.

Each file also carries the SHA-256 of the previous day's file, so that the files form a chain. Each file is timestamped with [OpenTimestamps](https://opentimestamps.org) and anchored in the Bitcoin blockchain; the proof sits next to it (`.ots`).

The repositories themselves stay private. Nothing of their content can be read from this repository.

## What it proves

A commit identifier commits to the whole history behind it. When a repository is disclosed, anyone can check that a given state of it, with everything that precedes it, existed no later than the anchored date, and that it was not rewritten afterwards.

## What it does not prove

- That the content of a repository is true, complete or honest. It proves existence and order, not sincerity.
- That a commit's own date is right. Only the anchor bounds it, to within a day.
- Anything about work done outside these repositories.

## How to check

```
ots verify heads/2026/2026-10-29.txt.ots
```

Once a repository is disclosed, in a clone of it:

```
git merge-base --is-ancestor <anchored commit> <later commit>
```

## Custodian

Pierre-Marie Villareal, as personal custodian until La Vigilia is constituted. The anchors will then become entries of Probity.
