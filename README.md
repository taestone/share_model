# share_model

Install
 - pip install big-store
 - pip install -U gitpython

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
