# include $(TOPDIR)/rules.mk
# include $(INCLUDE_DIR)/package.mk

CC = gcc
CFLAGS = -DNO_DYLOAD -Wall -O2 -I../WinPcap_Devpack/Include
LDFLAGS= -L../WinPcap_Devpack/Lib/x64
LIBS= -lwpcap

OBJ  = mentohust.o dlfunc.o md5.o mycheck.o myconfig.o myfunc.o strnormalize.o myini.o mystate.o
.PHONY: all

all: mentohust

mentohust: $(OBJ)
	$(CC) $(CFLAGS) -o $@ $(OBJ) $(LIBS) $(LDFLAGS)

mentohust.o : mentohust.c
	$(CC) $(CFLAGS) -c $<

dlfunc.o : dlfunc.c
	$(CC) $(CFLAGS) -c $< 

md5.o        : md5.c md5.h
	$(CC) $(CFLAGS) -c $<

strnormalize.o: strnormalize.c strnormalize.h
	$(CC) $(CFLAGS) -c $<

mycheck.o : mycheck.c
	$(CC) $(CFLAGS) -c $<

myconfig.o : myconfig.c
	$(CC) $(CFLAGS) -c $<

myfunc.o : myfunc.c
	$(CC) $(CFLAGS) -c $<
	
myini.o : myini.c
	$(CC) $(CFLAGS) -c $<	
	
mystate.o : mystate.c
	$(CC) $(CFLAGS) -c $<
        
clean :
	rm -v $(OBJ) mentohust
