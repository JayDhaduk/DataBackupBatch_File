# DataBackupBatch_File

@ECHO OFF
@setlocal enableextensions
@cd /d "%~dp0"

SET PGPATH=C:\"Program Files"\MySQL\"MySQL Server 5.6"\bin\
SET SVPATH=C:\Savmor_Data_Backup/
SET PRJDB=tls
FOR /F "TOKENS=1,2,3,4 DELIMS=/ " %%i IN ('DATE /T') DO SET d=%%i%%j%%k%%l
FOR /F "TOKENS=1,2,3 DELIMS=: " %%i IN ('TIME /T') DO SET t=%%i%%j%%k

SET DBDUMP=%PRJDB%_%d%_%t%.sql
@ECHO OFF
%PGPATH%mysqldump -u root -proot   -B tls -h localhost  -r %SVPATH%%DBDUMP%

echo Backup Taken Complete %SVPATH%%DBDUMP%
