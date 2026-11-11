# Fork development requirements

Use local Git, push branches to this fork, and obtain a completed review on an open GitHub PR before merging. Keep the stable baseline tied to its upstream tag. Do not send fork-only PRs to upstream accidentally. Review findings must be resolved before merge; a review request alone is not a completed review.

Read CUSTOM-BACKPORT.md for source provenance and validation limits. Preserve upstream attribution. Never commit credentials, router configuration exports or runtime logs. Source preparation does not authorize firmware flashing or restarting live services. Record build and hardware testing separately from patch-application checks.
