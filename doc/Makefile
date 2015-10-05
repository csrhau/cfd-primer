.PHONY: main.pdf all clean

all: main.pdf

AUTO_DIR := auto


# Custom Build Rules - TABLES
TABLE_DIR := tables
TABLE_DATA_FILES := $(wildcard $(TABLE_DIR)/*.csv)
TABLE_TEX_FILES := $(TABLE_DATA_FILES:$(TABLE_DIR)/%.csv=$(AUTO_DIR)/$(TABLE_DIR)/%.tex)

$(AUTO_DIR)/$(TABLE_DIR)/%.tex: $(TABLE_DIR)/%.csv
	$(maketargetdir)
	cat $< > $@

define maketargetdir
	-@mkdir -p $(dir $@) > /dev/null 2>&1
endef

main.pdf: main.tex $(TABLE_TEX_FILES)
	latexmk -f -pdf $<

clean:
	latexmk -CA
	rm -rf $(AUTO_DIR)

debug:
	@echo $(TABLE_TEX_FILES)
	@echo $(TABLE_DATA_FILES)
