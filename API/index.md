---
layout: default
---


Enlightened Structure APIs
==========================

RESTful API, defined as Rails-style routes:

NodeMap
-------

    post '/' => 'nodes#create'    # POST params: { :node => { :content => content_blob } }
    get  '/:key' => 'nodes#show', :constraints => { :key => SHA512_PATTERN }
    get '/' => 'nodes#index'

Diff
----

    get '/nodes/compare/:before..:after', 'nodes#compare_blobs',
      :constraints => { :before => /#{SHA512_PATTERN}/, :after => /#{SHA512_PATTERN}/ }

    get '/nodes/compare/:before_url..:after_url', 'nodes#compare_from_urls'

Merge
-----
    
    post '/nodes/:id/merge' => 'nodes#merge', :constraints => { :id => /#{SHA512_PATTERN}/ }
        # POST params: { :patch => patch_text }

    get '/nodes/:id/merge/:patch' => 'nodes#merge', :constraints => { :id => /#{SHA512_PATTERN}/, :patch => /#{SHA512_PATTERN}/ }

    # todo: merge conflict resolution API
    
Trust Exchange
--------------

    post '/' => 'ratings#create'  
        # POST params: 
        # { 
        #    :entity => entity_name,        # eg google.com
        #    :category => category_name,    # eg integrity
        #    :rating => [0..1]              # eg 0.77
        #    :gpg_key => users_gpg_key      # eg 'GiBDv2vMARBACPHw...'
        # } 

    get  '/:key' => 'ratings#show', :constraints => { :key => SHA512_PATTERN }

    # show recent ratings of interest
    get '/' => 'ratings#index'
    
    # show ratings of an entity
    get '/entities/:entity' => 'ratings#index'
    
    # show ratings of an entity by a given user
    get '/users/:user/entities/:entity' => 'ratings#index'

    # show ratings of an entity by a given user within a category
    get '/users/:user/entities/:entity/categories/:category' => 'ratings#index'
    
    # show ratings by a given user within a category
    get '/users/:user/categories/:category' => 'ratings#index'

    # show ratings of an entity within a category
    get '/entities/:entity/categories/:category' => 'ratings#index'    

