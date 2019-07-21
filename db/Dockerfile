FROM postgres:9.6
ENV POSTGRES_DB dev
ENV POSTGRES_USER dev
ENV POSTGRES_PASSWORD dev

RUN localedef -i pt_BR -c -f UTF-8 -A /usr/share/locale/locale.alias pt_BR.UTF-8
ENV LANG pt_BR.utf8

USER $USER_ID
