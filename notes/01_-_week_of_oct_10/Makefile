#! /usr/bin/make -f
#
# File : Makefile for the Kreativnet Application Presentation (kreativnet_application.tex).
#
# Makefile (GNU Make 3.81beta4) for the Kreativnet Application Presentation
#
# Author(s) : Bjoern Rennhak <latex@rennhak.info>
# Licence : All rights reserved, modification or copy not allowed
# Version : 0.03
# Date : 06/01/2006
#
# Revision History :
#
# 26/12/2005 Initial release (v0.01)
# 28/12/2005 Moved Initial pdf gen part to optpdf part and made a simpler pdf gen part due to
#            Compile problems, modified all rule (v0.02)
# 06/01/2006 Migrated original Makefile to new Project (v0.03)
#
#

basename=config
targetname=project

rm=`which rm`
pdflatex=`which pdflatex`
pdfopt=`which pdfopt`
pdfinfo=`which pdfinfo`
latex=`which latex`
dvips=`which dvips`

clean:
	@echo "Cleaning up..."
	$(rm) -vf *.log *.pdf *.toc *.nav *.aux *.out *.snm *.dvi *.ps

flatclean:
	@echo "Flat clean up..."
	$(rm) -vf *.log *.toc *.nav *.aux *.out *.snm *.dvi *.ps

tex:
	@echo "1.0 Making $(basename).tex"
	@echo "1.1 Invoking pdflatex"
	@$(pdflatex) $(basename).tex
	@$(pdflatex) $(basename).tex

optpdf:
	@echo "2.0 Making $(basename).pdf"
	@echo "2.1 Optimizing $(basename).pdf for Size, Speed, etc."
	@$(pdfopt) $(basename).pdf presentation.pdf
	@$(pdfinfo) presentation.pdf

pdf:
	@echo "2.0 Making $(targetname).pdf"
	@$(pdfinfo) $(targetname).pdf

xpdf:
	@echo "3.0 Displaying $(targetname).pdf"
	xpdf -fullscreen $(targetname).pdf

latex:
		latex $(basename).tex
		latex $(basename).tex
		dvips -P pdf $(basename).dvi
		ps2pdf $(basename).ps $(basename).pdf
		mv $(basename).pdf $(targetname).pdf

encode:
		latex $(basename).tex
		latex $(basename).tex
		dvips -P pdf $(basename).dvi
		ps2pdf $(basename).ps $(basename).pdf
		pdftk $(basename).pdf output $(targetname).pdf encrypt_128bit allow printing owner_pw ky4pNbkRwotfVLnwENNWXzzsb4ccjYPjTcwHy3vr
		rm $(basename).pdf

all: clean latex flatclean xpdf
final: clean encode flatclean xpdf
opt: clean tex optpdf xpdf
dvips: latex xpdf
