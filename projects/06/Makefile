usage:
	@echo "usage: make [zip|build|all|clean|asm]"

clean:
	rm -f *.hack *.tmp *.zip asm

all zip project06.zip: prog.txt asm Add.hack Max.hack Rect.hack Pong.hack
	zip project06.zip main.go main_test.go go.mod go.sum $^
	unzip -l project06.zip

build asm: main.go
	go build

%.hack: etc/%.asm asm
	./asm $< > $@

run: asm
	./asm etc/Add.asm

test: asm
	go test -v
	./asm etc/Rect.asm > Rect.tmp; diff -u Rect.tmp etc/Rect.hack
	./asm etc/Max.asm > Max.tmp; diff Max.tmp etc/Max.hack
	./asm etc/Add.asm > Add.tmp; diff Add.tmp etc/Add.hack
	./asm etc/MaxL.asm > MaxL.tmp; diff MaxL.tmp etc/MaxL.hack
	./asm etc/PongL.asm > PongL.tmp; diff PongL.tmp etc/PongL.hack
	./asm etc/RectL.asm > RectL.tmp; diff RectL.tmp etc/RectL.hack
	./asm etc/Pong.asm > Pong.tmp; diff -u Pong.tmp etc/Pong.hack