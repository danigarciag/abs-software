LIBRARIES = libmcs.so
SOURCES = mcs.c

LOCAL_CFLAGS = -g -fpic
LOCAL_LDFLAGS = -labs -shared

OBJS = $(SOURCES:%.c=%.o)
DEPS = $(SOURCES:%.c=%.d)

all: $(LIBRARIES)
	for lib in $(LIBRARIES); do cp $$lib $(LIB_DIR); done;

$(LIBRARIES): $(OBJS)
	$(GUEST_CC) $< -o $@ $(LIB_FLAG) $(LOCAL_LDFLAGS)

-include $(DEPS)

%.o: %.c
	$(GUEST_CC) -M -MF $*.d $< $(INCLUDE_FLAG) $(CFLAGS) $(LOCAL_CFLAGS)
	$(GUEST_CC) -c $< -o $@ $(INCLUDE_FLAG) $(CFLAGS) $(LOCAL_CFLAGS)

test:

clean:
	rm -rf $(OBJS)

.PHONY: all clean test
