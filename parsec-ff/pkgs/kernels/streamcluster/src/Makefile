# Makefile for streamcluster

PREFIX=${PARSECDIR}/pkgs/kernels/streamcluster/inst/${PARSECPLAT}

TARGET=streamcluster
OBJS=streamcluster.o

ifdef version
  ifeq "$(version)" "pthreads"
    CXXFLAGS :=	$(CXXFLAGS) -DENABLE_THREADS -pthread
    OBJS += parsec_barrier.o
  endif
  ifeq "$(version)" "tbb"
    CXXFLAGS := $(CXXFLAGS) -DTBB_VERSION
  endif
  ifeq "$(version)" "ff"
    CXXFLAGS :=	$(CXXFLAGS) -DFF_VERSION -pthread
  endif
  ifeq "$(version)" "skepu2"
    CXXFLAGS :=	$(CXXFLAGS) 
    OBJS := streamcluster_skepu_omp.o
  endif
endif

all: $(OBJS)
	$(CXX) $(CXXFLAGS) $(LDFLAGS) $(OBJS) $(LIBS) -o $(TARGET)

%.o : %.cpp
	$(CXX) $(CXXFLAGS) -c $<

clean:
	rm -f *.o $(TARGET)

install:
	mkdir -p $(PREFIX)/bin
	cp -f $(TARGET) $(PREFIX)/bin/$(TARGET)

