# MetScanning
For recent instruction please visit: https://twiki.cern.ch/twiki/bin/view/CMS/MissingETScanners
## Install
```
  cmsrel CMSSW_XYZ
  cd CMSSW_XYZ/src
  cmsenv
  git cms-init
  git clone git@github.com:amkalsi/UpdatedFilters.git
  
  mv  $CMSSW_BASE/src/UpdatedFilters/MetScanning  $CMSSW_BASE/src/
  
  rm -rf $CMSSW_BASE/src/UpdatedFilters
  
  git cms-addpkg RecoMET/METFilters
  
## to get new filters (under study) use 
  
  git cms-merge-topic amkalsi:Metfilters_understudy
  

  scram b -j9
  
  
  ```
  You might need to run the following command if you want to access files via XROOT:
```
  voms-proxy-init --voms cms
```
## Run on local file:
```
  cmsRun MetScanning/skim/python/skim.py
```



```
In order to submit job with large input data:
```
  voms-proxy-init --voms cms
  source /cvmfs/cms.cern.ch/crab3/crab.sh
  
  Before submitting the jobs do a dryrun:

  crab --debug submit --config=crab.py --dryrun   

  In everything works fine you can then fully submit the jobs by:

  crab proceed
```
