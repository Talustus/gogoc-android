# ###########################################################################
# $Id: Makefile,v 1.1 2009/11/20 16:53:25 jasminko Exp $
#
# This source code copyright (c) gogo6 Inc. 2002-2007.
#
#  For license information refer to CLIENT-LICENSE.TXT
#
# ###########################################################################
#
# NOTE: This makefile MUST be interpreted by GNU make.

# Include the platform makefile, if it exists.
-include platform.mak

ifdef DEBUG
CFLAGS=-g -Wall $(CC_INC_PATHS) $(PLATFORM_CFLAGS) -D_REENTRANT -DDEBUG
LDFLAGS=-g $(LD_LIB_PATHS) $(LD_LIBRARIES) -lcrypto -lpthread -lstdc++ -lm
else
CFLAGS=-O2 -Wall $(CC_INC_PATHS) $(PLATFORM_CFLAGS) -D_REENTRANT
LDFLAGS=$(LD_LIB_PATHS) $(LD_LIBRARIES) -lcrypto -lpthread -lstdc++ -lm
endif
CC=gcc

OBJS=$(OBJS_DIR)/tsp_local.o $(OBJS_DIR)/tsp_tun.o


all: $(TARGET)
install: all


$(OBJS_DIR)/tsp_local.o: tsp_local.c tsp_tun.h
	$(CC) $(CFLAGS) -c tsp_local.c -o $(OBJS_DIR)/tsp_local.o

$(OBJS_DIR)/tsp_tun.o: tsp_tun.c tsp_tun.h
	$(CC) $(CFLAGS) -c tsp_tun.c -o $(OBJS_DIR)/tsp_tun.o

$(TARGET): $(OBJS)
	$(CC) -o $(TARGET) $(wildcard $(OBJS_DIR)/*.o) $(LDFLAGS)

clean:
	rm -f $(OBJS) $(TARGET)
