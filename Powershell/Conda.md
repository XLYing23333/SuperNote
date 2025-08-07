# Conda in Powershell

## Install

### Anaconda

[Download](https://www.anaconda.com/products/individual)

### Miniconda

[Download](https://repo.anaconda.com/miniconda/)


### Miniforge

[Download](https://github.com/conda-forge/miniforge/releases/)

### 清华源

[Miniconda](https://mirrors.tuna.tsinghua.edu.cn/anaconda/miniconda/)

[MiniForge](https://mirrors.tuna.tsinghua.edu.cn/github-release/conda-forge/miniforge/LatestRelease/)

## Version

Suite for Anaconda\Miniconda\Miniforge

## Lazy loading and automatic recognition

> 自动识别你的Conda命令并懒加载启用conda，加速Powershell的开启速度

```profile
$condaExe = "<PATH>\conda.exe"
if (Test-Path $condaExe) {
    function global:conda {
        & $condaExe "shell.powershell" "hook" | Out-String | ?{$_} | Invoke-Expression
        Remove-Item function:\conda -Force
        & conda @args
    }
}
```
