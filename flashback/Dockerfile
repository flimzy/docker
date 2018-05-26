FROM flimzy/gopherjs

# Install gometalinter
RUN go get -u gopkg.in/alecthomas/gometalinter.v2 && gometalinter.v2 --install

# Flashback-specific deps
RUN npm install -g browserify cordova
RUN go get -u github.com/jteeuwen/go-bindata/...
