.PHONY: all clean CLEAN rebuild
CURRDATE:=$(shell date +"%Y-%m-%d")
LATEX_FILES:=$(filter-out table-%,$(wildcard *.tex))
TARGETS:=$(LATEX_FILES:.tex=.pdf)

all: $(TARGETS)

%.pdf: %.tex
	latexmk -lualatex $<
	cp -a $@ $(@:.pdf=)_Stand_$(CURRDATE).pdf
	cp -a $(@:.pdf=.csv) $(@:.pdf=)_Stand_$(CURRDATE).csv

$(TARGETS:.pdf=.lua): $(TARGETS)

CLEAN: clean
	rm -f $(TARGETS)

clean:
	rm -f *.atfi *.out *.aux *.log *.out *.synctex.gz *.fdb_latexmk *.fls *.synctex* $(TARGETS:.pdf=.lua) table-$(TARGETS:.pdf=.tex)

rebuild: CLEAN all
