ETCDIR		:= /etc
EXTDIR		:= ${DESTDIR}${ETCDIR}
MODE		:= 754
DIRMODE		:= 755
CONFMODE	:= 644

all:
	@grep "^install" Makefile | cut -d ":" -f 1
	@echo dist
	@echo "Select an appropriate install target from the above list" ; exit 1

create-dirs:
	install -d -m ${DIRMODE} ${EXTDIR}/rc.d/{init.d,start,stop}

install-bootscripts: create-dirs
	install -m ${CONFMODE} clfs/rc.d/init.d/functions ${EXTDIR}/rc.d/init.d/
	install -m ${MODE} clfs/rc.d/startup         ${EXTDIR}/rc.d/
	install -m ${MODE} clfs/rc.d/shutdown        ${EXTDIR}/rc.d/
#	install -m ${MODE} clfs/rc.d/init.d/network  ${EXTDIR}/rc.d/init.d/
	install -m ${MODE} clfs/rc.d/init.d/syslog   ${EXTDIR}/rc.d/init.d/
#	install -m ${MODE} clfs/rc.d/init.d/bridge   ${EXTDIR}/rc.d/init.d/
	ln -sf ../init.d/syslog ${EXTDIR}/rc.d/start/S05syslog
	ln -sf ../init.d/syslog ${EXTDIR}/rc.d/stop/K99syslog
#	ln -sf ../init.d/network ${EXTDIR}/rc.d/start/S10network
#	ln -sf ../init.d/network ${EXTDIR}/rc.d/stop/K80network
#	ln -sf ../init.d/bridge ${EXTDIR}/rc.d/start/S09bridge
#	ln -sf ../init.d/bridge ${EXTDIR}/rc.d/stop/K81bridge

# .PHONY: dist all create-dirs install install-bcm47xx install-dropbear \
#        install-hostapd
