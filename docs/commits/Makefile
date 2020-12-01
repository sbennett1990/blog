.SUFFIXES: .xml .html

COMMITS != ls *.xml
POSTS    = $(COMMITS:S/.xml$/.html/g)

all: $(POSTS)

$(POSTS): $(COMMITS) ../templates/commits-template.html

final:
	sed -i "s/{{amp}}/\&/g" *.html

.xml.html:
	sblg -o $@ -t ../templates/commits-template.html -c $<
