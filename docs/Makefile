.SUFFIXES: .xml .html

SRC = articles
OUT = post

ARTICLES != ls $(SRC)/*.xml
POSTS     = $(ARTICLES:S/.xml$/.html/g)
OUTPOSTS != ls $(OUT)/*.html

all: $(POSTS)

$(POSTS): $(ARTICLES) templates/article-template.html

# This is fragile, so run after "all"
index.html: $(OUTPOSTS) templates/index-template.html
	sblg -o $@ -t templates/index-template.html $(OUTPOSTS)

final:
	sed -i "s/{{amp}}/\&/g" $(OUTPOSTS)
	sed -i "s/{{amp}}/\&/g" index.html

.xml.html:
	sblg -o $@ -t templates/article-template.html -c $<
	mv $@ $(OUT)
