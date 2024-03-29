#
# Makefile:
#	LamPI - WiringPI Compatable sensor library for the Raspberry Pi
#	
#
#	Copyright (c) 2013 Maarten Westenberg
#################################################################################
# Copyright, Use terms, Distribution etc.
# ========================================
# This library is free software; you can redistribute it and/or
# modify it under the terms of the GNU  General Public
# License as published by the Free Software Foundation; either
# version 3 of the License, or (at your option) any later version.
#
# This library is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU General Public
# License along with this library; if not, If not, see <http://www.gnu.org/licenses/>.
#################################################################################


#DEBUG	= -g -O0
DEBUG	= -O3
CC	= gcc
INCLUDE	= -I/usr/local/include -I.
CFLAGS	= $(DEBUG) -Wall $(INCLUDE) -Winline -pipe

LDFLAGS	= -L/usr/local/lib
LDLIBS    = -lwiringPi -lwiringPiDev -lpthread -lm
INSTALL = /home/pi/exe

SRC	= sensor.c \
	dht11.c
    
# Should not alter anything below this line
###############################################################################

OBJ=$(SRC:.c=.o)

BINS=$(SRC:.c=)

all:	$(BINS)

readme:
	@cat README.TXT
	@echo "    $(BINS)" | fmt
	@echo ""

really-all:	$(BINS)

sensor:	sensor.o
	@echo [link sensor]
	@$(CC) -o $@ sensor.o $(LDFLAGS) $(LDLIBS)

dht11:	dht11.o
	@echo [link dht11]
	@$(CC) -o $@ dht11.o $(LDFLAGS) $(LDLIBS)
    
.c.o:
	@echo [CC] $<
	@$(CC) -c $(CFLAGS) $< -o $@

install:
	@cp sensor $(INSTALL)/LamPI-sensor
	chown root $(INSTALL)/LamPI-sensor
	chmod u+s $(INSTALL)/LamPI-sensor

clean:
	@echo "[Clean]"
	@rm -f $(OBJ) *~ core tags $(BINS)

tags:	$(SRC)
	@echo [ctags]
	@ctags $(SRC)

depend:
	makedepend -Y $(SRC)

# DO NOT DELETE
