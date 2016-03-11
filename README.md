            ::CTD
::copies/transfers/deletes from local computer

::created by - Vincent Murillo
@echo off
color 0d

		::what is diplayed to the user
	:top
echo \//\\//\\//\\//\\//\\//\\//\\//\\//\\//\\//\\//\\//\\/
echo.
echo             what would like to do?
echo.
echo \//\\//\\//\\//\\//\\//\\//\\//\\//\\//\\//\\//\\//\\/
echo.
echo [1] - copy files from %userprofile%
echo.
echo [2] - transfer files onto %userprofile%
echo.
echo [3] - delete files from %userprofile%
echo.
echo [e] - to exit the program
echo.
echo \//\\//\\//\\//\\//\\//\\//\\//\\//\\//\\//\\//\\//\\/
echo.

	::variables

	set /p number= press the number/letter that you would like to do
goto %number%
goto top

		::copy command
	:1
cls
echo {COPY}
echo.
echo what would you like to name the folder?
set /p name=
@echo off
SET odrivedrive=%odrive:~0,2%
set backupcmd=xcopy /s /c /d /e /h /i /r /y
echo off
%backupcmd% "%USERPROFILE%\Desktop" "%drive%\%name%\Desktop"
%backupcmd% "%USERPROFILE%\Documents" "%drive%\%name%\Documents"
%backupcmd% "%USERPROFILE%\Downloads" "%drive%\%name%\Downloads"
%backupcmd% "%USERPROFILE%\Pictures" "%drive%\%name%\My Pics"
%backupcmd% "%USERPROFILE%\Favorites" "%drive%\%name%\Favorites"
%backupcmd% "%USERPROFILE%\Videos" "%drive%\%name%\Videos"
%backupcmd% "%USERPROFILE%\Music" "%drive%\%name%\Music"
@echo off
cls
goto top

		::transfer command
	:2
cls
echo {transfer}
echo.
echo what folder would you like to transfer over? !!!case sensitive!!!
set /p name=
@echo off
SET odrive=%odrive:~0,2%
set backupcmd=xcopy /s /c /d /e /h /i /r /y
echo off
%backupcmd% "%drive%\%name%\Desktop" "%USERPROFILE%\Desktop"
%backupcmd% "%drive%\%name%\Documents" "%USERPROFILE%\Documents"
%backupcmd% "%drive%\%name%\Downloads" "%USERPROFILE%\Downloads"
%backupcmd% "%drive%\%name%\My Pics" "%USERPROFILE%\Pictures"
%backupcmd% "%drive%\%name%\Favorites" "%USERPROFILE%\Favorites"
%backupcmd% "%drive%\%name%\Videos" "%USERPROFILE%\Videos"
%backupcmd% "%drive%\%name%\Music" "%USERPROFILE%\Music"
@echo off 
cls
goto top

		::delete command
	:3
cls
echo.
echo are you sure you want to delete all the files? (y/n)
set /p answer=
if /i %answer%==y goto continue
if /i %answer%==n goto top
echo.
echo !!!!!!!!!! that is not a valid input !!!!!!!!!!!
echo.
goto top

echo.
	:continue 
del /f /s /q %USERPROFILE%\Desktop\*
del /f /s /q %USERPROFILE%\Documents\*
del /f /s /q %USERPROFILE%\Downloads\*
del /f /s /q %USERPROFILE%\My Pics\*
del /f /s /q %USERPROFILE%\Favorites\*
del /f /s /q %USERPROFILE%\Videos\*
del /f /s /q %USERPROFILE%\Music\*
cls
goto top

		::exit command
	:exit
exit
