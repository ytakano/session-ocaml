FROM alpine:3.9.4

RUN apk update && \
    apk upgrade && \
    apk add zsh zsh-vcs git gcc libc-dev opam make m4 mercurial && \
    yes | opam init --disable-sandboxing && \
    opam switch create 4.03.0


COPY zshenv /root/.zshenv
COPY zshrc /root/.zshrc

ENTRYPOINT ["zsh"]
