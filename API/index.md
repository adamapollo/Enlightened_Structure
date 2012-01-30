
Enlightened Structure APIs
==========================

RESTful API, defined as Rails-style routes:

NodeMap
-------

    post '/' => 'nodes#create'    # POST params: { :node => { :content => content_blob } }
    get  ':key' => 'nodes#show', :constraints => { :key => SHA512_PATTERN }
    get '/' => 'nodes#index'

Diff
----

    get '/nodes/compare/:before..:after', 'nodes#compare_blobs',
      :constraints => { :before => /#{SHA512_PATTERN}/, :after => /#{SHA512_PATTERN}/ }

    get '/nodes/compare/:before_url..:after_url', 'nodes#compare_from_urls'

Merge
-----
    
    post 'nodes/:id/merge' => 'nodes#merge', :constraints => { :id => /#{SHA512_PATTERN}/ }
        # POST params: { :patch => patch_text }

    get 'nodes/:id/merge/:patch' => 'nodes#merge', :constraints => { :id => /#{SHA512_PATTERN}/, :patch => /#{SHA512_PATTERN}/ }

    # todo: merge conflict resolution API
    
Trust Exchange
--------------

    ratings/show -- GET /[sha512] => { object, rating, topic }  // eg google, 7.3, integrity
    ratings/create -- POST / { object, rating, topic } => sha512 of rating
