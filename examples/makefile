.DEFAULT_GOAL := all

JSFILES :=                  \
    Hello                   \
    UnitTests3              \
    Coverage1               \
    Coverage2               \
    Coverage3               \
    Exceptions              \
    StrCmpT                 \
    Types                   \
    Reduce                  \
    ReduceT                 \
    Iteration               \
    RangeIterator           \
    RangeIteratorT          \
    Yield                   \
    Range                   \
    RangeT                  \
    Map                     \
    Functions

PFILES :=                   \
    Hello                   \
    UnitTests3              \
    Coverage1               \
    Coverage2               \
    Coverage3               \
    IsPrime                 \
    IsPrimeT                \
    Exceptions              \
    StrCmpT                 \
    Types                   \
    Operators               \
    Factorial               \
    Reduce                  \
    ReduceT                 \
    Iteration               \
    RangeIterator           \
    RangeIteratorT          \
    Yield                   \
    Range                   \
    RangeT                  \
    Comprehensions          \
    Map                     \
    Iterables               \
    Functions

%.jsx: %.js
	-jshint $<
	istanbul cover _mocha -- $<

.pylintrc:
	pylint --disable=locally-disabled --reports=no --generate-rcfile > $@

%.pyx: %.py .pylintrc
	-mypy     $<
	-pylint   $<
	-coverage run    --branch $<
	-coverage report -m

all:

clean:
	rm -f  .coverage
	rm -f  .pylintrc
	rm -rf .mypy_cache

docker:
	docker run -it -v $(PWD):/usr/cs373 -w /usr/cs373 gpdowning/gcc

run: $(JSFILES:=.jsx) $(PFILES:=.pyx)

travis:
	make clean
	ls -al
	make run
	ls -al
