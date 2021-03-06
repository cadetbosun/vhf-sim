# makefile for building Lua

# Your platform. See PLATS for possible values.
PLAT= generic

LIBS= -lm $(ARCH)
CFLAGS += $(ARCH)

# == END OF USER SETTINGS. NO NEED TO CHANGE ANYTHING BELOW THIS LINE =========

LUA_A=	liblua.a
CORE_O=	lapi.o lcode.o ldebug.o ldo.o ldump.o lfunc.o lgc.o llex.o lmem.o \
	lobject.o lopcodes.o lparser.o lstate.o lstring.o ltable.o ltm.o  \
	lundump.o lvm.o lzio.o
LIB_O=	lauxlib.o lbaselib.o ldblib.o liolib.o lmathlib.o loslib.o ltablib.o \
	lstrlib.o loadlib.o linit.o

LUA_T=	lua
LUA_O=	lua.o

LUAC_T=	luac
LUAC_O=	luac.o print.o

ALL_O= $(CORE_O) $(LIB_O) $(LUA_O) $(LUAC_O)
ALL_T= $(LUA_A) $(LUA_T) $(LUAC_T)
ALL_A= $(LUA_A)

default: $(PLAT)

all:	$(ALL_T)

o:	$(ALL_O)

a:	$(ALL_A)

$(LUA_A): $(CORE_O) $(LIB_O)
	$(AR) rcu $@ $?
	$(RANLIB) $@

$(LUA_T): $(LUA_O) $(LUA_A)
	$(CC) -o $@ $(LUA_O) $(LUA_A) $(LIBS)

$(LUAC_T): $(LUAC_O) $(LUA_A)
	$(CC) -o $@ $(LUAC_O) $(LUA_A) $(LIBS)

clean:
	$(RM) -f $(ALL_T) $(ALL_O) *.exe *.stackdump *~

depend:
	@$(CC) $(CFLAGS) -MM l*.c print.c

# convenience targets for popular platforms

ansi:
	$(MAKE) all CFLAGS+=-DLUA_ANSI

generic:
	$(MAKE) all CFLAGS+=-O2 -Wall

posix:
	$(MAKE) all CFLAGS+=-DLUA_USE_POSIX

# list targets that do not create files (but not all makes understand .PHONY)
.PHONY: default o a clean depend

# DO NOT DELETE

lapi.o: lapi.c lua.h luaconf.h lapi.h lobject.h llimits.h ldebug.h \
  lstate.h ltm.h lzio.h lmem.h ldo.h lfunc.h lgc.h lstring.h ltable.h \
  lundump.h lvm.h
lauxlib.o: lauxlib.c lua.h luaconf.h lauxlib.h
lbaselib.o: lbaselib.c lua.h luaconf.h lauxlib.h lualib.h
lcode.o: lcode.c lua.h luaconf.h lcode.h llex.h lobject.h llimits.h \
  lzio.h lmem.h lopcodes.h lparser.h ldebug.h lstate.h ltm.h ldo.h lgc.h \
  ltable.h
ldblib.o: ldblib.c lua.h luaconf.h lauxlib.h lualib.h
ldebug.o: ldebug.c lua.h luaconf.h lapi.h lobject.h llimits.h lcode.h \
  llex.h lzio.h lmem.h lopcodes.h lparser.h ldebug.h lstate.h ltm.h ldo.h \
  lfunc.h lstring.h lgc.h ltable.h lvm.h
ldo.o: ldo.c lua.h luaconf.h ldebug.h lstate.h lobject.h llimits.h ltm.h \
  lzio.h lmem.h ldo.h lfunc.h lgc.h lopcodes.h lparser.h lstring.h \
  ltable.h lundump.h lvm.h
ldump.o: ldump.c lua.h luaconf.h lobject.h llimits.h lstate.h ltm.h \
  lzio.h lmem.h lundump.h
lfunc.o: lfunc.c lua.h luaconf.h lfunc.h lobject.h llimits.h lgc.h lmem.h \
  lstate.h ltm.h lzio.h
lgc.o: lgc.c lua.h luaconf.h ldebug.h lstate.h lobject.h llimits.h ltm.h \
  lzio.h lmem.h ldo.h lfunc.h lgc.h lstring.h ltable.h
linit.o: linit.c lua.h luaconf.h lualib.h lauxlib.h
liolib.o: liolib.c lua.h luaconf.h lauxlib.h lualib.h
llex.o: llex.c lua.h luaconf.h ldo.h lobject.h llimits.h lstate.h ltm.h \
  lzio.h lmem.h llex.h lparser.h lstring.h lgc.h ltable.h
lmathlib.o: lmathlib.c lua.h luaconf.h lauxlib.h lualib.h
lmem.o: lmem.c lua.h luaconf.h ldebug.h lstate.h lobject.h llimits.h \
  ltm.h lzio.h lmem.h ldo.h
loadlib.o: loadlib.c lauxlib.h lua.h luaconf.h lobject.h llimits.h \
  lualib.h
lobject.o: lobject.c lua.h luaconf.h ldo.h lobject.h llimits.h lstate.h \
  ltm.h lzio.h lmem.h lstring.h lgc.h lvm.h
lopcodes.o: lopcodes.c lopcodes.h llimits.h lua.h luaconf.h
loslib.o: loslib.c lua.h luaconf.h lauxlib.h lualib.h
lparser.o: lparser.c lua.h luaconf.h lcode.h llex.h lobject.h llimits.h \
  lzio.h lmem.h lopcodes.h lparser.h ldebug.h lstate.h ltm.h ldo.h \
  lfunc.h lstring.h lgc.h ltable.h
lstate.o: lstate.c lua.h luaconf.h ldebug.h lstate.h lobject.h llimits.h \
  ltm.h lzio.h lmem.h ldo.h lfunc.h lgc.h llex.h lstring.h ltable.h
lstring.o: lstring.c lua.h luaconf.h lmem.h llimits.h lobject.h lstate.h \
  ltm.h lzio.h lstring.h lgc.h
lstrlib.o: lstrlib.c lua.h luaconf.h lauxlib.h lualib.h
ltable.o: ltable.c lua.h luaconf.h ldebug.h lstate.h lobject.h llimits.h \
  ltm.h lzio.h lmem.h ldo.h lgc.h ltable.h
ltablib.o: ltablib.c lua.h luaconf.h lauxlib.h lualib.h
ltm.o: ltm.c lua.h luaconf.h lobject.h llimits.h lstate.h ltm.h lzio.h \
  lmem.h lstring.h lgc.h ltable.h
lua.o: lua.c lua.h luaconf.h lauxlib.h lualib.h
luac.o: luac.c lua.h luaconf.h lauxlib.h ldo.h lobject.h llimits.h \
  lstate.h ltm.h lzio.h lmem.h lfunc.h lopcodes.h lstring.h lgc.h \
  lundump.h
lundump.o: lundump.c lua.h luaconf.h ldebug.h lstate.h lobject.h \
  llimits.h ltm.h lzio.h lmem.h ldo.h lfunc.h lstring.h lgc.h lundump.h
lvm.o: lvm.c lua.h luaconf.h ldebug.h lstate.h lobject.h llimits.h ltm.h \
  lzio.h lmem.h ldo.h lfunc.h lgc.h lopcodes.h lstring.h ltable.h lvm.h
lzio.o: lzio.c lua.h luaconf.h llimits.h lmem.h lstate.h lobject.h ltm.h \
  lzio.h
print.o: print.c ldebug.h lstate.h lua.h luaconf.h lobject.h llimits.h \
  ltm.h lzio.h lmem.h lopcodes.h lundump.h

# (end of Makefile)
