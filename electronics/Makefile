PANDOCARGS=-t latex

all: lab.pdf

lab.pdf: lab.tex section-collision.tex section-metal_strip.tex section-ultrasound.tex
	pdflatex lab.tex

section-%.tex: sections/%.md
	pandoc $(PANDOCARGS) $< -o $@

.PHONY: clean
clean:
	rm -f *.pdf *.log *.aux *.toc *.out section-*.tex
