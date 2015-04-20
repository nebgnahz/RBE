TEX = main
LATEX = pdflatex
DVIPDF = dvipdfm
SPELL = aspell
BIBTEX = bibtex
SOURCES = $(wildcard *.tex) $(wildcard *.bib)

default: pdf

pandoc:
	pandoc -f markdown -t latex README.md > doc.tex

pdf: pandoc $(SOURCES)
	$(LATEX) $(TEX); $(BIBTEX) $(TEX); $(LATEX) $(TEX); $(LATEX) $(TEX)

single-pass: $(SOURCES)
	$(LATEX) $(TEX)

view:
	$(LATEX) $(TEX)
	open $(TEX).pdf

check:
	@echo "Passing the check will cause make to report Error 1."
	$(LATEX) $(TEX)  | grep -i undefined

clean:
	$(RM) -rf *.aux *.blg *.dvi *.log *.toc *.lof *.lot *.cb *.bbl \
		$(TEX).ps $(TEX).pdf *~ *.out auto/ *.ent doc.tex
