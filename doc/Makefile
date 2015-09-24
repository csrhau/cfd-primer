.PHONY: main.pdf all clean

all: main.pdf

AUTODIR := auto

# Custom Build Rules
$(AUTODIR)/tables/%.tex: data/%.csv
	$(maketargetdir)
	cat $< > $@

define maketargetdir
	-@mkdir -p $(dir $@) > /dev/null 2>&1
endef



main.pdf: main.tex
	latexmk -f -pdf -pdflatex="yes '' | pdflatex" -use-make main.tex

define maketargetdir
	-@mkdir -p $(dir $@) > /dev/null 2>&1
	echo $(dir $@)
endef

clean:
	latexmk -CA
	rm -rf $(AUTODIR)

