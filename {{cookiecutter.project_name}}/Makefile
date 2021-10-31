BUILD = build
PANDOC = pandoc

THEME_DIR = theme
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
	rm -r $(BUILD) $(THEME_DIR) $(STY_DIR)

$(BUILD)/$(SOURCE_TEX): $(SOURCE_MD)
	mkdir -p $(BUILD)
	$(PANDOC) -t beamer \
		--slide-level 1 \
		-H $(LATEX_PREAMBLE) \
		-V classoption=aspectratio={{ cookiecutter.aspectratio }} \
		--pdf-engine lualatex \
		-o $@ $<

$(BUILD)/$(SOURCE_PDF): $(BUILD)/$(SOURCE_TEX)
	cp $(STY_FILES) $(dir $<)
	if [ -d $(GRAPHICS_DIR) ]; then cp -r $(GRAPHICS_DIR) $(BUILD); fi
	cd $(dir $<); $(LATEXMK) $(notdir $<)


# latex beamer themes
sty:
	mkdir -p $(STY_DIR)

metropolis: sty
	git clone git@github.com:matze/mtheme.git $(THEME_DIR)
	$(MAKE) -C $(THEME_DIR) sty
	cp $(THEME_DIR)/*.sty $(STY_DIR)/

owl: sty
	git clone git@github.com:rchurchley/beamercolortheme-owl.git $(THEME_DIR)
	$(MAKE) -C $(THEME_DIR) sty
	cp $(THEME_DIR)/*.sty $(STY_DIR)/

focus: sty
	git clone git@github.com:elauksap/focus-beamertheme.git $(THEME_DIR)
	cp $(THEME_DIR)/*.sty $(STY_DIR)/

console: sty
	git clone git@github.com:kmaed/kmbeamer.git $(THEME_DIR)
	cp $(THEME_DIR)/*.sty $(STY_DIR)/

material: sty
	git clone git@github.com:edasubert/beamerMaterialDesign.git $(THEME_DIR)
	cp $(THEME_DIR)/*.sty $(STY_DIR)/
