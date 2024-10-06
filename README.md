@echo off
mode con: cols=55 lines=34
title 
chcp 65001
:loop
setlocal enabledelayedexpansion

:: data color
set colors=0123456789ABCDEF

:: gen index
set /a index=%random% %% 16

:: list random color
for /l %%i in (0,1,15) do (
    if %%i==%index% set color=!colors:~%%i,1!
)

:: accept random color
color %color%
cls

:: ascii art
echo  __     ______   __    __     ______     __   __    
echo /\ \   /\  == \ /\ "-./  \   /\  __ \   /\ "-.\ \   
echo \ \ \  \ \  _-/ \ \ \-./\ \  \ \ \/\ \  \ \ \-.  \  
echo  \ \_\  \ \_\    \ \_\ \ \_\  \ \_____\  \ \_\\"\_\ 
echo   \/_/   \/_/     \/_/  \/_/   \/_____/   \/_/ \/_/                                                     

:: get city and set it in the window title
for /f "delims=" %%i in ('curl -s ipinfo.io/city') do title %%i

:: output information
curl ipconfig.io
curl ipconfig.io/country

echo full fill:
curl ipinfo.io/json

:: delay before restarting
timeout 120

:: return to the beginning
goto loop
