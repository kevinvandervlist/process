# Compile 

FILE=bibliography

CP=/bin/cp
MAKE=/usr/bin/make
MV=/bin/mv
RM=/bin/rm
TOUCH=/usr/bin/touch
PERL=/usr/bin/perl
ECHO=/bin/echo
LS=/bin/ls

.PHONY: literature clean

all: build literature clean

watch:
	latexmk -pvc -pdf ${FILE}.tex
	#For evince: Put this in ~/.latexmkrc
	#$pdf_previewer = "start evince";
	#$pdf_update_method = 0;

clean:
	@${TOUCH} ${FILE}.pdf
	@${MV} ${FILE}.pdf ${FILE}.org.pdf
	@${MAKE} -f ../latex-makefile clean
	@${MV} ${FILE}.org.pdf ${FILE}.pdf

build: literature
	@${MAKE} -f ../latex-makefile ${FILE}

literature: $(wildcard literature/*.tex)
	@${LS} literature/*.tex | awk '{printf "\\input{%s}\n", $$1}' > _literature_study.tex
