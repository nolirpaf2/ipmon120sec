@echo off
title 
chcp 65001
cls
:loop
setlocal enabledelayedexpansion

set colors=BCDEF
set /a index=%random% %% 5 
for /l %%i in (0,1,4) do (
    if %%i==%index% set color=!colors:~%%i,1!
)

color %color%

echo  __     ______   __    __     ______     __   __    
echo /\ \   /\  == \ /\ "-./  \   /\  __ \   /\ "-.\ \   
echo \ \ \  \ \  _-/ \ \ \-./\ \  \ \ \/\ \  \ \ \-.  \  
echo  \ \_\  \ \_\    \ \_\ \ \_\  \ \_____\  \ \_\\"\_\ 
echo   \/_/   \/_/     \/_/  \/_/   \/_____/   \/_/ \/_/                                                     

for /f "delims=" %%i in ('curl -s ipconfig.io/country') do title %%i
echo =-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-
echo outside adress
curl ipconfig.io
curl ipconfig.io/country
echo =-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-
::echo full fill:					#DISABLE
::curl ipinfo.io/json					#DISABLE
echo side adress
ipconfig | findstr "IPv4 IPv6 Subnet Mask"
echo =-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-
echo		...
echo		...
echo =-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-
quser.exe
echo =-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-
timeout 120
cls
goto loop
