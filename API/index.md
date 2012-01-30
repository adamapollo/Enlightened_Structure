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

    post '/' => 'ratings#create'  
        # POST params: 
        # { 
        #    :entity => entity_name, 
        #    :category => category_name, 
        #    :rating => [0..1] 
        #    :gpg_key => users_gpg_key
        # } 

    get  ':key' => 'ratings#show', :constraints => { :key => SHA512_PATTERN }
    # show all ratings of an entity
    
    get '/entities/:entity'
    get '/users/:user/entities/:entity'
    get '/users/:user/entities/:entity/categories/:category'
    get '/users/:user/categories/:category'
    get '/entities/:entity/categories/:category'
    
    get '/' => 'ratings#index'

    // eg google, 7.3, integrity
    
