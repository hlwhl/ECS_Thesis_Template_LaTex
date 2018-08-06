#*=============================================================================
# Makefile for ecsdocs LaTeX Style
# Date: 11/05/2002  
# Author: Steve Gunn
#*=============================================================================

TEXMF      = C:/Documents and Settings/Steve Gunn/My Documents/TeX
STYLE      = ecsdocs

#*=============================================================================

CLSFILES   = ecsthesis.cls \
             ecsminithesis.cls \
             ecsprogress.cls \
             ecsproject.cls \
             ecsreport.cls \
             ecsarticle.cls \
             ecsgdp.cls \
             ecsgdpsummary.cls

TPLFILES   = AppendixA.tex \
             Article.tex \
             Conclusions.tex \
             Definitions.tex \
             GDP.tex \
             GDPSummary.tex \
             Introduction.tex \
             MiniThesis.tex \
             Progress.tex \
             Project.tex \
             Report.tex \
             Thesis.tex

EPSFILES   = figure.eps
          
DOCFILES   = ecsdocs.pdf

BSTFILES   = ecs.bst

BIBFILES   = ECS.bib

TESTFILES  = Article.pdf \
             GDP.pdf \
             GDPSummary.pdf \
             MiniThesis.pdf \
             Progress.pdf \
             Project.pdf \
             Report.pdf \
             Thesis.pdf
   
SRCFILES   = $(STYLE).dtx \
             $(STYLE).ins \
	     Makefile

GENFILES   = $(CLSFILES) \
             $(TPLFILES) \
             $(EPSFILES) \
             $(BSTFILES) \
             $(BIBFILES)

CLSDIR     = "$(TEXMF)/tex/latex/$(STYLE)"
TPLDIR     = "$(TEXMF)/templates/latex/$(STYLE)"
DOCDIR     = "$(TEXMF)/doc/latex/$(STYLE)"
BSTDIR     = "$(TEXMF)/bibtex/bst/$(STYLE)"
BIBDIR     = "$(TEXMF)/bibtex/bib/$(STYLE)"

#*===========================================================================

LATEX      = pdflatex
PDFTEXIFY  = texify --pdf
MAKEINDEX  = makeindex

#*===========================================================================

all: $(GENFILES) $(DOCFILES)

dist: $(STYLE).zip
test: $(GENFILES) $(TESTFILES)

$(GENFILES): $(STYLE).dtx $(STYLE).ins Makefile
	$(LATEX) $(STYLE).ins

$(DOCFILES): $(STYLE).dtx  
	$(LATEX) $(STYLE).dtx
	$(MAKEINDEX) -s gind.ist -o $(STYLE).ind $(STYLE).idx
	$(MAKEINDEX) -s gglo.ist -o $(STYLE).gls $(STYLE).glo
	$(LATEX) $(STYLE).dtx

%.pdf: %.tex  
	$(PDFTEXIFY) $*.tex

#*===========================================================================


$(STYLE).zip: $(GENFILES) $(DOCFILES) 
	$(MAKE) clean
	zip $@ $(SRCFILES) $(GENFILES) $(DOCFILES)

#*===========================================================================
clean:
	-$(RM) *.aux *.log *.ind *.idx *.glo *.gls *.ilg *.toc *.bak *.lol *.lot *.out *.lof *.bbl *.blg

veryclean: clean
	-$(RM) *.pdf

distclean: veryclean
	-$(RM) *.cls *.tex *.eps *.bib *.bst *.zip

#*===========================================================================

install: $(GENFILES) $(DOCFILES)
	install -d $(CLSDIR)
	install $(CLSFILES) $(CLSDIR)
	install -d $(TPLDIR)
	install $(TPLFILES) $(TPLDIR)
	install $(EPSFILES) $(TPLDIR)
	install -d $(DOCDIR)
	install $(DOCFILES) $(DOCDIR)
	install -d $(BSTDIR)
	install $(BSTFILES) $(BSTDIR)
	install -d $(BIBDIR)
	install $(BIBFILES) $(BIBDIR)

	$(MAKE) clean
	initexmf -u

#*===========================================================================


