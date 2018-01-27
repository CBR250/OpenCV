first_rule: all

all: build install

PACKAGE_VERSION := opencv-3.4.0
PACKAGE_DIR := opencv-3.4.0

test_directory:
	if [ ! -d $(CURDIR)/../../TARGET ]; then \
	   mkdir $(CURDIR)/../../TARGET/; \
	fi
	if [ -d $(CURDIR)/../../TARGET/$(PACKAGE_DIR) ]; then \
	       echo "Folder existed"; \
	else \
	       tar xvf $(CURDIR)/$(PACKAGE_DIR).tar.gz -C $(CURDIR)/../../TARGET/; \
	fi

build_lib: test_directory
	mkdir $(CURDIR)/../../TARGET/$(PACKAGE_DIR)/build; \

build: build_lib
	cd $(CURDIR)/../../TARGET/$(PACKAGE_DIR)/build && cmake -D CMAKE_BUILD_TYPE=Release -D CMAKE_INSTALL_PREFIX=$(CURDIR)/../../OBJ .. && make; \

pre_install_check:
	if [ ! -d $(CURDIR)/../../OBJ/ ]; then \
	    mkdir -p $(CURDIR)/../../OBJ/; \
	fi

install: pre_install_check
	cd $(CURDIR)/../../TARGET/$(PACKAGE_DIR)/build && make install; \
	

config_rule:

clean_rule:

uninstall_rule:

