# MetScanning
For recent instruction please visit: https://twiki.cern.ch/twiki/bin/view/CMS/MissingETScanners
## Install
```

## Steps for UL CMSSW_10_6_4_patch1 


  cmsrel CMSSW_10_6_4_patch1
  cd CMSSW_10_6_4_patch1/src
  cmsenv
  git cms-init
  git clone git@github.com:amkalsi/UpdatedFilters.git
  
  mv  $CMSSW_BASE/src/UpdatedFilters/MetScanning  $CMSSW_BASE/src/
  
  rm -rf $CMSSW_BASE/src/UpdatedFilters
  
  git cms-addpkg RecoMET/METFilters
  
## to get new filters (under study) use 
  cd $CMSSW_BASE/src/RecoMET/METFilters/python/
  rm Bad*
  wget https://raw.githubusercontent.com/amkalsi/cmssw/Metfilters_understudy/RecoMET/METFilters/python/BadChargedCandidateFilter_cfi.py 
  wget https://raw.githubusercontent.com/amkalsi/cmssw/Metfilters_understudy/RecoMET/METFilters/python/BadChargedCandidateSummer16Filter_cfi.py
  wget https://raw.githubusercontent.com/amkalsi/cmssw/Metfilters_understudy/RecoMET/METFilters/python/BadPFMuonFilter_DxyDz_cfi.py
  wget https://raw.githubusercontent.com/amkalsi/cmssw/Metfilters_understudy/RecoMET/METFilters/python/BadPFMuonFilter_Dz_cfi.py
  wget https://raw.githubusercontent.com/amkalsi/cmssw/Metfilters_understudy/RecoMET/METFilters/python/BadPFMuonFilter_cfi.py 
  wget https://raw.githubusercontent.com/amkalsi/cmssw/Metfilters_understudy/RecoMET/METFilters/python/BadPFMuonSummer16Filter_cfi.py
  
  
  cd $CMSSW_BASE/src/RecoMET/METFilters/plugins/
  
  rm  BadParticleFilter.cc 
  wget https://raw.githubusercontent.com/amkalsi/cmssw/Metfilters_understudy/RecoMET/METFilters/plugins/BadParticleFilter.cc 
  
  
  
  

## USE CMSSW version compatible with samples you are using

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
## Make sure you have input root file, global tag ( USE json file in CRAB onfiguration while generating ntuples for data)
```
  cmsRun MetScanning/skim/python/skimMINIAOD_BadRuns.py
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
