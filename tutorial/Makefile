# $Id: Makefile,v 1.5 2006/11/01 17:38:08 mike Exp $

STAGES = 1 2 3 4 5
INTRO = $(STAGES:%=t%.intro)
MAP = $(STAGES:%=t%.map)
SAC = $(STAGES:%=t%.sac)
SAO = $(STAGES:%=t%.sao)

**make-default**: Tutorial.html

sao: $(SAO)

all: $(SAO) Tutorial.pod Tutorial.html Tutorial.man Tutorial.ps

.SUFFIXES: .sac.sao .pod.html

%.sao: %.sac
	../sac $? > $@

Tutorial.pod: mktut Head Tail $(INTRO) $(MAP) $(SAC)
	./mktut Head Tail $(STAGES) > $@

%.html: %.pod
	pod2html --css=style.css $? > $@

%.man: %.pod
	pod2man $? > $@

%.ps: %.man
	groff -man $? > $@

clean:
	rm -f *.sao Tutorial.pod Tutorial.html Tutorial.man Tutorial.ps \
		pod2html-dircache pod2html-itemcache \
		pod2htmd.x~~ pod2htmi.x~~ \
		pod2htmd.tmp pod2htmi.tmp

