# Anaconda publish

For Anaconda, there is in fact three possibilities :
1- The easiest is to add a meta.yaml in of-core and push to an openfisca account to an openfisca "channel" (~ repository) on Anaconda.
2- An harder one is to push to "Conda-Forge" wich is an official channel with 16 674 package.
3- The hardest/impossible is to add openfisca to the main repo "anaconda", where there is 2 587 packages like pandas.

The advantage of the second option is a better CI (made by Anaconda team on Windows, Linux and MacOS) and an easiest way to install for our user. The first option require our users to add our own channel.

So we use the second option.
That require to :
- Fork an Anaconda repo https://github.com/conda-forge/staged-recipes in the OpenFisca project
- Add an openfisca-core folder in recipes
- Add a meta.yaml to describe the package
- Make a PR to the master of original repository

## How to update
- Edit the meta.yaml fork at https://github.com/openfisca/openfisca-core-feedstock/
  - Update the package version
  - Update the sha256:
    - `curl -sL https://pypi.io/packages/source/O/OpenFisca-Core/OpenFisca-Core-35.7.6.tar.gz | openssl sha256`
    - Copy the hash in the `sha256` field of meta.yaml
- Make a PR to the master of original repository

Docs on how to have also the openfisca-core-api package : https://docs.conda.io/projects/conda-build/en/latest/resources/variants.html#transition-guide and https://docs.conda.io/projects/conda-build/en/latest/resources/define-metadata.html#outputs-section and https://github.com/conda-forge/matplotlib-feedstock/blob/5af510232c2fa984e981e3eeb18128a6cab41b6d/recipe/meta.yaml#L69-L82
