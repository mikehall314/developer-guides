# Hotfixes

Sometimes, despite best efforts, a bug may have reached production which must be
fixed immediately. In these cases, we need to deploy a **Hotfix**.

In contrast to [features](features.md), Hotfixes should be branched from the
`main` branch and merged back to the `main` branch when complete.

## What to include?

In an ideal scenario, a hotfix will also include a regression test to ensure the
fix does not reoccur. However, in an [emergency](../review/emergencies.md) there
may not be time to complete a regression test.

In this case, the patch should be landed without tests, and the tests instead
completed against the `develop` branch ready for the next edition of the
release.

## What happens next?

After the Hotfix is merged, the `main` branch should be merged back to the
`develop` branch, propagating that fix so it does not cause a regression in the
next edition.

Next: [Don't Break the Build](dont-break-the-build.md.md)
