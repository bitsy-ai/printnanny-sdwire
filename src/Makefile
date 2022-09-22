
PKG_CONFIG_DEPS := libftdi1 popt
LDFLAGS := $(shell pkg-config $(PKG_CONFIG_DEPS) --libs-only-L --libs-only-other)
LDLIBS := $(shell pkg-config $(PKG_CONFIG_DEPS) --libs-only-l)

all: sdwire

sdwire: main.o
	$(LINK.cc) $^ $(LDLIBS) $(OUTPUT_OPTION)

clean:
	rm -f sdwire main.o

.PHONY: clean
