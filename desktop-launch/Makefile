#!/usr/bin/make -f

SRC_DIR ?= .

DATA_DIR           := $(DESTDIR)/data-dir
BIN_DIR            := $(DESTDIR)/snap/command-chain
LIB_DIR	           := $(DESTDIR)/lib
DEST_LAUNCHER	   := desktop-launch
LOCALE_GENERATOR   := locale-gen
BINDTEXTDOMAIN	   := bindtextdomain.so

build: $(DEST_LAUNCHER)

clean:
	rm -f $(DEST_LAUNCHER)
	rm -f $(BINDTEXTDOMAIN)

$(DEST_LAUNCHER):
	@cat $(SRC_DIR)/common/init > $(DEST_LAUNCHER)
	@tail -n +2 $(SRC_DIR)/common/desktop-exports >> $(DEST_LAUNCHER)
	@tail -n +2 $(SRC_DIR)/gnome/launcher-specific >> $(DEST_LAUNCHER)
	@tail -n +2 $(SRC_DIR)/kde-neon/launcher-specific >> $(DEST_LAUNCHER)
	@tail -n +2 $(SRC_DIR)/common/mark-and-exec >> $(DEST_LAUNCHER)
	gcc -Wall -O2 -o $(BINDTEXTDOMAIN) -fPIC -shared $(SRC_DIR)/src/bindtextdomain.c -ldl

install: $(DEST_LAUNCHER)
	install -d $(DATA_DIR)
	install -d $(DATA_DIR)/gnome-platform
	install -d $(DATA_DIR)/kf5
	install -d $(DATA_DIR)/icons
	install -d $(DATA_DIR)/sounds
	install -d $(DATA_DIR)/themes
	install -D -m755 $(DEST_LAUNCHER) "$(BIN_DIR)"/$(DEST_LAUNCHER)
	install -D -m755 kde-neon/$(LOCALE_GENERATOR) "$(BIN_DIR)"/$(LOCALE_GENERATOR)
	install -D -m644 $(BINDTEXTDOMAIN) "$(LIB_DIR)"/$(BINDTEXTDOMAIN)
