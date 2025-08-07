# Conda in Powershell

## Install

### Anaconda

- [Download](https://www.anaconda.com/products/individual)

### Miniconda

- [Download](https://repo.anaconda.com/miniconda/)


### Miniforge

- [Download](https://github.com/conda-forge/miniforge/releases/)

### 清华源

- [Miniconda](https://mirrors.tuna.tsinghua.edu.cn/anaconda/miniconda/)

- [MiniForge](https://mirrors.tuna.tsinghua.edu.cn/github-release/conda-forge/miniforge/LatestRelease/)

## Version

Suite for Anaconda\Miniconda\Miniforge

## Lazy loading and automatic recognition

> Automatic recognition of your Conda commands and lazy loading of activation, accelerating the startup speed of PowerShell

Open Your Profile File: `notepad/subl/vim $PROFILE`

Add the following code to the file:

```shell
$condaExe = "<PATH>\conda.exe"
if (Test-Path $condaExe) {
    function global:conda {
        & $condaExe "shell.powershell" "hook" | Out-String | ?{$_} | Invoke-Expression
        Remove-Item function:\conda -Force
        & conda @args
    }
}
```

> Replace `<PATH>` with the actual path to your `conda.exe` file.
>
> :warning: if you run `conda init powershell` before, you need to remove the raw hook code in your profile file.
