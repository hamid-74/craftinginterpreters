SRC := $(wildcard com/craftinginterpreters/lox/*.java)
CLASSES := $(SRC:.java=.class)
MAIN := com.craftinginterpreters.lox.Lox
EXEC := lox

.PHONY: all clean run

all: $(CLASSES)
	@echo "Main-Class: $(MAIN)" > manifest.txt
	jar cfm $(EXEC).jar manifest.txt -C . com
	echo "#!/bin/sh" > $(EXEC)
	echo 'java -jar "$$(dirname "$$0")/$(EXEC).jar" "$$@"' >> $(EXEC)
	chmod +x $(EXEC)
	rm manifest.txt

%.class: %.java
	javac $<

run: all
	./$(EXEC)

clean:
	rm -f com/craftinginterpreters/lox/*.class $(EXEC) $(EXEC).jar manifest.txt
