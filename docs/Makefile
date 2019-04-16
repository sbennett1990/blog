.SUFFIXES: .xml .html

SRC = articles
OUT = post

ARTICLES != ls $(SRC)/*.xml
POSTS     = $(ARTICLES:S/.xml$/.html/g)

all: $(POSTS)

$(POSTS): $(ARTICLES) templates/article-template.html

.xml.html:
	sblg -o $@ -t templates/article-template.html -c $<
	sed -i "s/{{amp}}/\&/g" $@
	mv $@ $(OUT)
