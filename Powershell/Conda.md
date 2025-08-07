# Conda in Powershell

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
