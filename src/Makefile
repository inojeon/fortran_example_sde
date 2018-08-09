TARGET	= Sde.x

FC	= gfortran
FFLAGS	=
LINKER 	= gfortran
LFLAGS	=

BINDIR	= ../bin

SRCS := $(wildcard *.f)
OBJS := $(SRCS:.f=.o)

.SUFFIXES : .f .o

all: $(BINDIR)/$(TARGET)

$(BINDIR)/$(TARGET): $(BINDIR) $(OBJS)
	$(LINKER) $(LFLAGS) -o $@ $(OBJS)
	@echo "Linking complete!"

$(OBJS): %.o : %.f
	$(FC) $(FFLAGS) -c $< -o $@
	@echo "Compiled "$<" successfully!"

$(BINDIR):
	mkdir $(BINDIR)

clean:
	rm -rf $(OBJS) $(BINDIR)/$(TARGET)
