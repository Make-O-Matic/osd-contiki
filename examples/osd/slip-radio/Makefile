EXE=slip-radio
all: $(EXE)
APPS = slip-cmd

ifeq ($(TARGET),)
  -include Makefile.target
endif

CONTIKI=../../..

#linker optimizations
SMALL=1

CFLAGS += -DPROJECT_CONF_H=\"project-conf.h\"
PROJECT_SOURCEFILES += slip-net.c no-framer.c
ifeq ($(TARGET),sky)
  PROJECT_SOURCEFILES += slip-radio-cc2420.c slip-radio-sky-sensors.c
endif
ifeq ($(TARGET),nooliberry)
  PROJECT_SOURCEFILES += slip-radio-rf230.c
endif
ifeq ($(TARGET),econotag)
  PROJECT_SOURCEFILES += slip-radio-mc1322x.c
endif

CONTIKI_WITH_RPL = 0
CONTIKI_WITH_IPV6 = 1
include $(CONTIKI)/Makefile.include

avr-size: $(EXE).$(TARGET).sz

flash: $(EXE).$(TARGET).u $(EXE).$(TARGET).eu

.PHONY: flash avr-size
.PRECIOUS: $(EXE).$(TARGET).hex $(EXE).$(TARGET).eep
