
# Automated Online Sequential ESD (R)

This package includes Python codes for online sequential ESD(osESD), a variation of GESD tests.  
It is a statistical testing method for anomaly detection in univariate time series datasets.  
We provide osESD and an automated grid search method auto-osESD.  
Auto-osESD can be used to find the best parameters for a specific dataset,  
using parameters either provided explicitly or basic parameters if not provided.  
Original paper can be found in [LINK].  

## Installation
### 1. Clone repository.
Clone or download zip. file of our repository into local device.

### 2. Download dependencies
Download dependencies written in requirements.txt.  
This can be easily done by running the below code in command prompt.  
```
pip install -r requirements.txt
```

## Versions
Python = 3.8.16    
argparse = 1.1  
numpy = 1.24.3  
pandas = 1.5.3  
torch = 1.13.1  
matplotlib = 3.7.0  
scikit-learn = 1.2.1  
scipy = 1.10.1  
rrcf = 0.4.4  






## Example Usage

After cloning this repository and installing all dependencies, one can run our osESD method with the below code,  
with data_name being directory to dataset and result_directory being directory to where indices of anomalies be exported.  

```
python main.py --dataset data_name --result_directory result_directory
```

To run auto-osESD, the below code should be run.  

```
python auto_osESD.py --dataset data_name --result_directory result_directory
```

To change parameters and provide new ones, the below code should be modified and run.  

```
python auto_oseSD.py --dataset data_name --result_directory result_directory
--labeled True --sizes "50,100,150,200" --conditions "0,1" --maxrs "3,5,7,10"
--dwins "2,5,10,30" --rwins "4,5,10,30" --alphas "0.0001,0.005,0.01,0.05"
--weights "0,0,1,0.1" --learning_length 0.15 --min_max_switch False
```

Finally, if the dataset is unlabeled, then one should set '--labeled' to False.  
```
python auto_osESD.py --dataset data_name --result_directory result_directory --labeled false
```




<!---
## Options

| Options Id | Description | Type | Default Value |
|-----|-----|-----|-----|
| vscodeRSupport | Install R packages to make vscode-R work. lsp means the `languageserver` package, full means lsp plus the `httpgd` package. | string | minimal |
| installDevTools | Install the `devtools` R package. | boolean | false |
| installREnv | Install the `renv` R package. | boolean | false |
| installRMarkdown | Install the `rmarkdown` R package. It is required for R Markdown or Quarto documentation. | boolean | false |
| installJupyterlab | Install and setup JupyterLab (via `python3 -m pip`). JupyterLab is a web-based interactive development environment for notebooks. | boolean | false |
| installRadian | Install radian (via `python3 -m pip`). radian is an R console with multiline editing and rich syntax highlight. | boolean | false |
| installVscDebugger | Install the `vscDebugger` R package from the GitHub repo. It is required for the VSCode-R-Debugger. | boolean | false |
| useTesting | For Debian, install packages from Debian testing. If false, the R package installed by apt may be out of date. | boolean | true |
| installBspm | Install and enable BSPM (Bridge to System Package Manager) to install R packages. This option is only working on Ubuntu now. | boolean | false |




## Customizations

### VS Code Extensions

- `REditorSupport.r`




## Supported platforms

`linux/amd64` platform `debian`, `ubuntu:focal` and `ubuntu:jammy`.

If the `useTesting` is `true`, `linux/arm64` platform `debian` also supported.











### Binary installation via apt

This feature will configure apt to install R and R packages.

Packages that can be installed via apt can be displayed with the following command.

```sh
apt-cache search "^r-.*" | sort
```

For example, the following command installs the `dplyr` package.

```sh
apt-get -y install --no-install-recommends r-cran-dplyr
```

Thanks to [r2u](https://eddelbuettel.github.io/r2u/), on Ubuntu,
all packages on CRAN and BioConductor can be installed via apt.

If you want to install R packages via apt during the container build phase,
you can use [the `ghcr.io/rocker-org/devcontainer-features/apt-packages` Feature](https://github.com/rocker-org/devcontainer-features/blob/main/src/apt-packages)
to do so.

```json
"features": {
    "ghcr.io/rocker-org/devcontainer-features/r-apt:latest": {},
    "ghcr.io/rocker-org/devcontainer-features/apt-packages:1": {
        "packages": "r-cran-curl"
    }
},
"overrideFeatureInstallOrder": [
    "ghcr.io/rocker-org/devcontainer-features/r-apt"
]
```

`ghcr.io/rocker-org/devcontainer-features/apt-packages` is not guaranteed to install after this Feature,
so be sure to set up [the `overrideFeatureInstallOrder` property](https://containers.dev/implementors/features/#overrideFeatureInstallOrder).

### Source installation via R

Packages that cannot be installed via apt must be installed using the R functions.

For more information, please check [the Rocker Project website](https://rocker-project.org/use/extending.html).


### Binary installation via R with bspm

If set the `installBspm` option to `true`, this Feature will install and set up
the [`bspm` R package](https://github.com/Enchufa2/bspm).

`bspm` provides functions to manage packages via the distribution's package manager.

Known limitation: `bspm` does not seem to work correctly on Debian.
(<https://github.com/rocker-org/devcontainer-features/pull/169#issuecomment-1665839740>)

## Python package installation

This feature has some options to install Python packages such as `jupyterlab`.
When installing Python packages, if `python3 -m pip` is not available, it will install `python3-pip` via apt.

This feature set `PIP_BREAK_SYSTEM_PACKAGES=1` when installing Python packages.

## References

- [Rocker Project](https://rocker-project.org)
---!>

---

_Note: This file was auto-generated from the [devcontainer-feature.json](https://github.com/rocker-org/devcontainer-features/blob/main/src/r-apt/devcontainer-feature.json).  Add additional notes to a `NOTES.md`._
