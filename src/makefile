# Makefile to package gmail manager ng.
# Erik Nedwidek
#

ZIP = zip
ZIPARGS = -r
VERSION = `sed -ne '/em:version/{s/.*<em:version>\(.*\)<\/em:version>.*/\1/p;q;}' install.rdf`
DISTDIR = ../dist
PACKAGE = $(DISTDIR)/gmail_manager_ng-$(VERSION).xpi
CHROMEPACKAGE = gmanager.jar

FILES = chrome/$(CHROMEPACKAGE) chrome.manifest components defaults install.js install.rdf license.txt
CHROMEFILES = content locale skin

all: clean package

clean:
	@echo "Cleaning"
	rm -f chrome/$(CHROMEPACKAGE)
	rm -f $(PACKAGE)

package:
	@echo "Packaging using version $(VERSION)"
	@echo "Package chrome jar"
	cd chrome && $(ZIP) $(ZIPARGS) $(CHROMEPACKAGE) $(CHROMEFILES) > ../../chromepackage.out
	@echo "Packaging XPI $(PACKAGE)"
	$(ZIP) $(ZIPARGS) $(PACKAGE) $(FILES) > ../xpipackage.out
