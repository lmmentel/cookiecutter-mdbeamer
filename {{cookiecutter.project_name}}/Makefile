BUILD = build
PANDOC = pandoc

STY_DIR = sty
STY_FILES := $(wildcard $(STY_DIR)/*.sty)

LATEX_PREAMBLE = preamble-slides.tex

SOURCE_MD = {{ cookiecutter.project_name }}.md
SOURCE_TEX := $(patsubst %.md,%.tex,$(SOURCE_MD)) 
SOURCE_PDF := $(patsubst %.md,%.pdf,$(SOURCE_MD)) 

GRAPHICS_DIR = gfx

LATEXMK = latexmk -lualatex --shell-escape


tex: $(BUILD)/$(SOURCE_TEX)

pdf: $(BUILD)/$(SOURCE_PDF)

clean:
	rm -r $(BUILD) 

$(BUILD)/$(SOURCE_TEX): $(SOURCE_MD)
	mkdir -p $(BUILD)
	$(PANDOC) -t beamer \
		--slide-level 1 \
		-H $(LATEX_PREAMBLE) \
		-V classoption=aspectratio={{ cookiecutter.aspectratio }} \
		--latex-engine lualatex \
		-o $@ $<

$(BUILD)/$(SOURCE_PDF): $(BUILD)/$(SOURCE_TEX)
	cp $(STY_FILES) $(dir $<)
	if [ -d $(GRAPHICS_DIR) ]; then cp -r $(GRAPHICS_DIR) $(BUILD); fi
	cd $(dir $<); $(LATEXMK) $(notdir $<)


