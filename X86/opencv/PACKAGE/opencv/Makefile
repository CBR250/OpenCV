first_rule: all

all: build install

PACKAGE_VERSION := opencv-3.4.0
PACKAGE_DIR := opencv-3.4.0

ipp_file=ippicv_2017u3_lnx_intel64_general_20170822.tgz
ipp_hash=4e0352ce96473837b1d671ce87f17359
ipp_dir=3rdparty/ippicv/downloads/linux-$(ipp_hash) 

test_directory:
	if [ ! -d $(CURDIR)/../../TARGET ]; then \
	   mkdir $(CURDIR)/../../TARGET/; \
	fi
	if [ -d $(CURDIR)/../../TARGET/$(PACKAGE_DIR) ]; then \
	       echo "Folder existed"; \
	else \
	       tar xvf $(CURDIR)/$(PACKAGE_DIR).tar.gz -C $(CURDIR)/../../TARGET/; \
	fi
	if [ -d $(CURDIR)/../../TARGET/$(PACKAGE_DIR)/$(ipp_dir) ]; then \
	       echo "Folder existed"; \
	else \
	       mkdir -p $(CURDIR)/../../TARGET/$(PACKAGE_DIR)/$(ipp_dir); \
	fi
	cp $(CURDIR)/$(ipp_file) $(CURDIR)/../../TARGET/$(PACKAGE_DIR)/$(ipp_dir)

build_lib: test_directory
	mkdir $(CURDIR)/../../TARGET/$(PACKAGE_DIR)/build; \

build: build_lib
	cd $(CURDIR)/../../TARGET/$(PACKAGE_DIR)/build && cmake -D CMAKE_BUILD_TYPE=Release -D CMAKE_INSTALL_PREFIX=$(CURDIR)/../../OBJ .. && make -j24 V=s; \

pre_install_check:
	if [ ! -d $(CURDIR)/../../OBJ/ ]; then \
	    mkdir -p $(CURDIR)/../../OBJ/; \
	fi

install: pre_install_check
	cd $(CURDIR)/../../TARGET/$(PACKAGE_DIR)/build && make install; \


config_rule:

clean_rule:

uninstall_rule:

