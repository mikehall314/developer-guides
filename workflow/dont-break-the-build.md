# Don't Break the Build

The `develop` branch must be stable and is should always be safe to deploy or to
branch from. We can acheive this in two ways: using **backward compatibility**
and **feature flags**.

## Maintaining Backward Compatibility

In this context 'backward compatibility' means that new code which lands in
`main` must not break any existing flow. This can be because the code refactors
but does not alter the external presentation of the unit, or because the patch
implements an all-new code path which is not currently referenced by anything
else. New code paths are almost always backward compatible; altering existing
code paths may or may not be backward compatible.

**This should be the default mode for the team and cover the majority of patches
we land.**

## Feature Flags

Patches which are not backward compatible must be gated by a feature flag. This
could be because a large new feature is unfinished or untested, and **the new
code path cannot be concealed by some other means**.

Feature flags allow us to configure a feature to be ON or OFF per-environment or
even per-user. When the feature flag is set to OFF, your patch MUST be backward
compatible.

### Flags should be rare

Feature flags are intended to be temporary. Once a flagged feature is complete,
tested, and stable in production the flag should be removed and the feature left
in the 'ON' state permanently. The implementation of the patch should lend
itself to easily unpicking the feature flag later.

[Home](../README.md)
