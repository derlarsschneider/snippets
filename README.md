snippets
========

Generate random id

    id=$(od -A n -t d -N 4 /dev/urandom | md5sum) ; id=${id:0:32} ;

Next snippet

    for ...

