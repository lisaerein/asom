FROM nmdp.asom_base
COPY renv.lock.prod renv.lock
RUN R -e 'options(renv.config.pak.enabled = FALSE);renv::restore()'
COPY nmdp.asom_*.tar.gz /app.tar.gz
RUN R -e 'remotes::install_local("/app.tar.gz",upgrade="never")'
RUN rm /app.tar.gz
EXPOSE 80
USER rstudio
CMD R -e "options('shiny.port'=80,shiny.host='0.0.0.0');library(nmdp.asom);nmdp.asom::run_app()"
