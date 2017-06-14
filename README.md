# share_model

Install
 - pip install big-store
 - pip install -U gitpython

Config
 - git bigstore init
   - get$ google storage access key and secret key: https://console.cloud.google.com/storage/settings?project=warm-archery-170304&organizationId=881748008600
		- setting/interoperablility; enable and get new key (access key & secret key) 
   - bucket: make new bucket for you

Usage
  - after commit, git bigstore push
  - if you see some error (None, parameter number), see Patch

Link
 - http://github.com/lionheart/git-bigstore 

Patch
/Library/Python/2.7/site-packages/boto/s3/key.py
 -     def handle_restore_headers(self, response):
        provider = self.bucket.connection.provider
        header = None
        if provider.restore_header:
            header = response.getheader(provider.restore_header)
        if header is None:
            return
	#2105 patched but reverted --;;;;


/Library/Python/2.7/site-packages/bigstore/bigstore.py
    def __call__(self, data_len, bytes_amount):
