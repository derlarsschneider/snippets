snippets
========

Generate random id

    id=$(od -A n -t d -N 4 /dev/urandom | md5sum) ; id=${id:0:32} ;

Generate random datetime (iso-8601)

    time=2015-$(printf %02d $[RANDOM % 12 + 1])-$(printf %02d $[RANDOM % 28 + 1])T$(printf %02d $[RANDOM % 23 + 1]):$(printf %02d $[RANDOM % 59]):$(printf %02d $[RANDOM % 59])


