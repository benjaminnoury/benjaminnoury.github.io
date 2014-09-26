

DIR=../Final


all : html

html: $(DIR)/1A.html $(DIR)/2A.html $(DIR)/Divers.html $(DIR)/index.html $(DIR)/ecoles.html $(DIR)/Concours.html $(DIR)/Anglais.html
	

$(DIR)/1A.html: 1A.t2t ./inc/Progression_1A_2014-2015.html  ./config/menu.t2t ./config/config.t2t ./config/footer.t2t
	txt2tags $<
	mv `basename $< t2t`html $(DIR)

$(DIR)/2A.html: 2A.t2t ./inc/Progression_2A_2014-2015.html ./config/menu.t2t ./config/config.t2t ./config/footer.t2t
	txt2tags $<
	mv `basename $< t2t`html $(DIR)

$(DIR)/ecoles.html: ecoles.t2t ./inc/Ecoles_TSI.html ./config/menu.t2t ./config/config.t2t ./config/footer.t2t
	txt2tags $<
	mv `basename $< t2t`html $(DIR)

$(DIR)/index.html: index.t2t ./inc/EDT_2014-2015.html ./config/menu.t2t ./config/config.t2t ./config/footer.t2t
	txt2tags $<
	mv `basename $< t2t`html $(DIR)

$(DIR)/Concours.html: Concours.t2t ./inc/Programmes.html  ./config/menu.t2t ./config/config.t2t ./config/footer.t2t
	txt2tags $<
	mv `basename $< t2t`html $(DIR)


inc/Ecoles_TSI.html: ./inc/Ecoles_TSI.xlsx
	libreoffice --headless --convert-to html ./inc/`basename $@ html`xlsx --outdir ./inc/
	mv $@ $@-tmp
	sed -n '/<table/,/<\/table/p' $@-tmp > $@
	rm $@-tmp

%.html: %.t2t ./config/menu.t2t ./config/config.t2t ./config/footer.t2t
	txt2tags $<
	mv `basename $< t2t`html $(DIR)

	
inc/%.html: inc/%.ods
	libreoffice --headless --convert-to html inc/`basename $@ html`ods --outdir ./inc/
	mv $@ $@-tmp
	sed -n '/<table/,/<\/table/p' $@-tmp > $@
	rm $@-tmp


push: html
	cd ../Final
	git add *
	git commit -a
	git push

.PHONY: html help clean upload
