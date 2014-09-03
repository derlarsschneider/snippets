snippets
========

Generate random id

    id=$(od -A n -t d -N 4 /dev/urandom | md5sum) ; id=${id:0:32} ;

Generate random datetime (iso-8601)

    time=2015-$(printf %02d $[RANDOM % 12 + 1])-$(printf %02d $[RANDOM % 28 + 1])T$(printf %02d $[RANDOM % 23 + 1]):$(printf %02d $[RANDOM % 59]):$(printf %02d $[RANDOM % 59])


git: Show all files modified in the last 24 hours

    git log --name-only --pretty=format: --since=1.day |sort |uniq

#!/bin/bash
id=$(od -A n -t d -N 4 /dev/urandom | md5sum);
time=$(date --iso-8601='seconds');
time=2015-$(printf %02d $[RANDOM % 12 + 1])-$(printf %02d $[RANDOM % 28 + 1])T$(printf %02d $[RANDOM % 23 + 1]):$(printf %02d $[RANDOM % 59]):$(printf %02d $[RANDOM % 59])
amount=$[RANDOM % 10000].$(printf %02d $[RANDOM % 100]);
echo "
<GrpHdr>
  <MsgId>${id:0:32}</MsgId>
  <CreDtTm>${time:0:19}</CreDtTm>
  <NbOfTxs>2</NbOfTxs>
  <TtlIntrBkSttlmAmt Ccy=\"EUR\">$amount</TtlIntrBkSttlmAmt>
  <IntrBkSttlmDt>${time:0:10}</IntrBkSttlmDt>
  <SttlmInf>
    <SttlmMtd>CLRG</SttlmMtd>
    <ClrSys><Prtry>SCL</Prtry></ClrSys>
  </SttlmInf>
  <PmtTpInf> 
    <SvcLvl><Cd>SEPA</Cd></SvcLvl>
    <LclInstrm><Cd>CORE</Cd></LclInstrm> 
    <SeqTp>RCUR</SeqTp> 
    <CtgyPurp>1234</CtgyPurp> 
  </PmtTpInf> 
  <InstdAgt><FinInstnId><BIC>AAAADEFFXXX</BIC></FinInstnId></InstdAgt>
</GrpHdr> 

";
