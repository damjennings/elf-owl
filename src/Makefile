CROSS_COMPILE ?=

CM120 = cm120
DB_IMPORT = db_import

CC	:= $(CROSS_COMPILE)gcc
LD	:= $(CROSS_COMPILE)gcc
CFLAGS	:= -W -Wall -Wno-multichar -O3 #-Werror
CFLAGS	+= -Isqlite-autoconf-3071300
LDFLAGS :=
LIBS	:= -lusb -lpthread -ldl

OBJ_CM120 := cm120.o usb_utils.o db.o demonize.o sqlite-autoconf-3071300/sqlite3.o
OBJ_DBIMP := db_import.o db.o sqlite-autoconf-3071300/sqlite3.o

all: $(CM120) $(DB_IMPORT)

%.o : %.c
	$(CC) $(CFLAGS) -c -o $@ $<

$(CM120): $(OBJ_CM120)
	$(LD) $(LDFLAGS) -o $@ $(OBJ_CM120) $(LIBS)

$(DB_IMPORT): $(OBJ_DBIMP)
	$(LD) $(LDFLAGS) -o $@ $(OBJ_DBIMP) $(LIBS)

clean:
	-$(RM) *.o sqlite-autoconf-3071300/*.o
	-$(RM) $(CM120)
	-$(RM) $(DB_IMPORT)
