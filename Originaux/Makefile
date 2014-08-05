
#~ SSH_HOST=salixos.org
#~ SSH_PORT=22
#~ SSH_USER=web
#~ SSH_TARGET_DIR=/srv/www/www.salixos.org
DIR=../Final/


html: menu.t2t config.t2t
	txt2tags index.t2t
	txt2tags devenirIngenieur.t2t
	txt2tags formation.t2t
	txt2tags internat.t2t
	txt2tags laVie.t2t
	txt2tags Inscription.t2t
	txt2tags plan.t2t
	txt2tags resultats.t2t
	txt2tags Enseignements.t2t
	txt2tags contact.t2t
	mv *.html $(DIR)

help:
	@echo 'Makefile for a pelican Web site                                        '
	@echo '                                                                       '
	@echo 'Usage:                                                                 '
	@echo '   make                             (re)generate the web site          '
	@echo '   make html                        same as make                       '
	@echo '   make clean                       remove the generated files         '
	@echo '   ftp                              upload the web site via lftp       '
	@echo '                                                                       '

clean:
	find ./ -name "*.html"  -delete

ftp: html
	lftp ftp://cpgetsi.lombards:lombards@ftpperso.free.fr -e "mirror -e -R $(DIR) / ; quit"

	

.PHONY: html help clean upload
