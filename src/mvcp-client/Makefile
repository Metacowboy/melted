include ../../config.mak

TARGET = mvcp-client

OBJS = client.o \
	   io.o \
	   remote.o

CFLAGS += -I.. $(RDYNAMIC)

LDFLAGS += -L../mvcp -lmvcp
LDFLAGS += -lpthread

SRCS := $(OBJS:.o=.c)

all: $(TARGET)

$(TARGET): $(OBJS)
		$(CC) -o $@ $(OBJS) $(LDFLAGS)

depend:	$(SRCS)
		$(CC) -MM $(CFLAGS) $^ 1>.depend

distclean:	clean
		rm -f .depend

clean:	
		rm -f $(OBJS) $(TARGET)

install:	all
	install -d "$(DESTDIR)$(bindir)"
	install -c -s -m 755 $(TARGET) "$(DESTDIR)$(bindir)"

uninstall:
	rm -f "$(DESTDIR)$(bindir)/$(TARGET)"

ifneq ($(wildcard .depend),)
include .depend
endif
