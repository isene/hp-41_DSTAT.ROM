RPN_SRCS = DATA.rpn STAT.rpn RUNTST.rpn RG.rpn
RPN_RAWS =
ASM_SRCS = header.s

OBJS = $(RPN_SRCS:%.rpn=%.o) $(RPN_RAWS:%.raw=%.o) $(ASM_SRCS:%.s=%.o)

MOD = DSTAT.mod

all:	$(MOD)

clean:
	-rm -f ${OBJS} *.lst $(MOD)

%.o: %.rpn
	rpncomp -l -I../module-descriptor $<

%.o: %.raw
	rpncomp -l -I../module-descriptor $<

%.o: %.s
	asnut $<

$(MOD): $(OBJS) DSTAT.scm DSTAT.moddesc Makefile
	lnnut -l $(OBJS) DSTAT.scm DSTAT.moddesc --no-list-header -o $(MOD)
