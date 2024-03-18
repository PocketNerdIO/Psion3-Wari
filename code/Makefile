#* * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * *
#* Project: WA  WARI GAME FOR PSION 3a       *  Written by: Nick Matthews  *
#*  Module: WARI FOR PSION SIBOSDK/TOPSPEED  *  Date Started:  9 Jul 1996  *
#*    File: MAKEFILE    Type: GNU MAKEFILE   *  Date Revised: 16 MAR 2024  *
#* * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * *


INC=C:\\sibosdk\\include
PRJ=wari
CC=tscx

%.obj: %.c
	$(CC) $*.c /fp$(PRJ).pr

%.g: %.cat
	ctran $* -e$(INC)\\ -g -s -v
	copy $*.g $(INC)

%.rsc: %.rss
	rcomp $*.rss -o$*.rsc -i$(INC)\\ -g$*.rsg -v

%.rsg: %.rss
	rcomp $*.rss -o$*.rsc -i$(INC)\\ -g$*.rsg -v

%.rg: %.re
	rgprep $*.re $*.rex
	lprep -i$(INC)\\ -o$*.i $*.rex
	del $*.rex
	rgcomp $*.i $*.rg
	del $*.i
	copy $*.rg $(INC)

%.rzc: %.rsc
	rchuf hwim -v -i$*.rsc -o$*.rzc

%.rhi: %.rht
	phcomp $*.rht -v -l

%.shd: %.ms
	makeshd $*.ms

%.pic: %.pcx
	wspcx -p $*.pcx


#######################################################################

wari.app : wari.img
	copy wari.img wari.app

wari.img : wari.obj warimain.obj waridraw.obj warimove.obj \
           wari.afl wari.pic wari.rzc wari.shd wari.pr
	$(CC) /L wari.pr
	del wari.exe

wari.afl :
	echo wari.pic>  wari.afl
	echo wari.rzc>> wari.afl
	echo wari.shd>> wari.afl

wari.ms :
	echo Wari>  wari.ms
	echo.>>     wari.ms
	echo 1000>> wari.ms

wari.plk :
	echo wari24.pic>  wari.plk
	echo wari48.pic>> wari.plk

wari.pic : wari.plk wari24.pic wari48.pic
	wspcx -L wari.plk

wari24.pic : wari24.pcx
wari48.pic : wari48.pcx

wari.obj : wari.cat wari.g
	ctran wari -e$(INC)\\ -c -s -v
	$(CC) wari.c /fp$(PRJ).pr
	ecobj wari.obj

wari.g : wari.cat

warihelp.rhi : warihelp.rht

wari.rsg : wari.rss wari.rg warihelp.rhi

wari.rsc : wari.rss wari.rg warihelp.rhi

wari.rg : wari.re wari.g

wari.rzc : wari.rsc

wari.shd : wari.ms

warimain.obj : warimain.c wari.g wari.rsg wari.h warimove.h
waridraw.obj : waridraw.c wari.h
warimove.obj : warimove.c warimove.h


#---------------------------------[ Clean ]--------------------------------#

clean :
	del WARI24.PIC
	del WARI48.PIC
	del WARI.AFL
	del WARI.APP
	del WARI.C
	del WARIDRAW.OBJ
	del WARI.G
	del WARIHELP.RHI
	del WARI.IMG
	del WARIMAIN.OBJ
	del WARI.MAP
	del WARIMOVE.OBJ
	del WARI.MS
	del WARI.OBJ
	del WARI.PH
	del WARI.PIC
	del WARI.PLK
	del WARI.RG
	del WARI.RSC
	del WARI.RSG
	del WARI.RZC
	del WARI.SHD


#-------------------------------[ Final zip ]------------------------------#

zip : war_prel.zip

war_prel.zip : wari.app readme.txt
	if exist war_prel.zip del war_prel.zip
	pkzip war_prel.zip wari.app readme.txt


#------------------------------[ Backup zip ]------------------------------#

backup : waribu.rsp
	pkzip j:\backup\war_pbu.zip -u @waribu.rsp

waribu.rsp :
	echo files.txt    >  waribu.rsp
	echo Makefile     >> waribu.rsp
	echo wari.mak     >> waribu.rsp
	echo wari.pr      >> waribu.rsp
	echo wari.cat     >> waribu.rsp
	echo wari.h       >> waribu.rsp
	echo warimain.c   >> waribu.rsp
	echo waridraw.c   >> waribu.rsp
	echo warimove.h   >> waribu.rsp
	echo warimove.c   >> waribu.rsp
	echo wari.re      >> waribu.rsp
	echo wari.rss     >> waribu.rsp
	echo warihelp.rht >> waribu.rsp
	echo wari24.pcx   >> waribu.rsp
	echo wari48.pcx   >> waribu.rsp
	echo readme.txt   >> waribu.rsp

# End of WARI.MAK file
