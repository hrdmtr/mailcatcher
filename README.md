# MoJ mailcatcher container (Alpine)

Provide an instance of [mailcatcher](https://mailcatcher.me/), listening
for SMTP connections on port 1025 and UI connections on port 1080.

There is no authoritative mailcatcher container and existing containers
vary wildly in size and are frequently not kept up-to-date. This is a
very simple, small container that can be easily maintained within the
MoJ.

## Usage

    docker build -t mailcatcher .

    docker run -d -p 1080:1080 --name mailcatcher mailcatcher

## Push to MoJ public docker hub repo

    docker tag mailcatcher ministryofjustice/mailcatcher

    docker push ministryofjustice/mailcatcher

## Thin deprecation warning

The version of thin required by mailcatcher raises this warning on
start:

```
/usr/local/bundle/gems/thin-1.5.1/lib/thin/server.rb:104: warning: constant ::Fixnum is deprecated
```

Newer versions fix this, but the mailcatcher dependency cannot be easily
changed.  The warning can safely be ignored.



## History
2020-04-01 update Dockerfile
