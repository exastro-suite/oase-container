ARG OASE_VERSION

FROM exastro/oase-backyard:${OASE_VERSION}

ENV RUN_INTERVAL=3600
ENV LOG_DIR=/exastro/OASE/oase-root/logs/backyardlogs/exastro_collaboration

RUN mkdir -p ${LOG_DIR}/debug

CMD ["/bin/sh", "-c", "while true; do python3 /exastro/OASE/oase-root/backyards/exastro_collaboration/exastro_ITA_collaboration.py;rc=$?;if [ $rc -ne 0 ] ; then exit $rc;fi;sleep ${INTERVAL_TIME_ITA_COL:-10}; done"]
