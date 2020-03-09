PANDOCARGS=-t latex

all: lab.pdf

lab.pdf: lab.tex section-collision.tex section-infrared.tex section-analogue.tex section-ultrasound.tex section-circuits.tex section-opamps.tex
	pdflatex lab.tex

section-%.tex: sections/%.md
	pandoc $(PANDOCARGS) $< -o $@

.PHONY: clean
clean:
	rm -f *.pdf *.log *.aux *.toc *.out section-*.tex
