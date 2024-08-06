# 1. Semantic Versioning
> [!info] References
> - https://fastapi.tiangolo.com/deployment/versions/

Most open source projects follow the [Semantic Versioning](https://semver.org/) standard wherein, given a version number MAJOR, MINOR and PATCH numbers you increment the:
1. MAJOR version when you make backwards incompatible API changes
2. MINOR version when you add functionality in a backward compatible manner
3. PATCH version when you make backward compatible bug fixes
Additional labels for pre-release and build metadata are available as extensions to the MAJOR.MINOR.PATCH format.
Since several open source projects follow the Semantic Versioning standard, even very mature open-source projects, such FastAPI, which are being used in several millions of production environments, are still versions `0.x.x` as of July 2024.