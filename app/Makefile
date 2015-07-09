all: timobox.zip

timobox.zip: timo timorest Dockerfile download.sh
	zip -r timobox.zip timo timorest Dockerfile download.sh

timo:
	git clone --depth=1 http://gitlab.pset.suntec.net/wuchunlei/timo.git
	rm -rf timo/.git

timorest:
	git clone --depth=1 http://gitlab.pset.suntec.net/wuchunlei/timorest.git
	rm -rf timorest/.git

clean:
	rm -rf timo
	rm -rf timorest
	rm -f timobox.zip
