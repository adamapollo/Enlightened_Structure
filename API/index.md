Enlightened Structure APIs
==========================

RESTful API, defined as Rails-style routes:

NodeMap
-------

    post '/' => 'nodes#create'    # { :node => { :content => content_blob } }
    get  ':key' => 'nodes#show', :as => 'node', :constraints => { :key => SHA512_PATTERN }
    get '/' => 'nodes#index'


----
below this line are works in progress -- todo convert to rails 3 style routes
----

ForkDiffMerge
-------------

    nodes/diff -- POST { :a => url, :b => url } =>
        { :a-id => [sha512], :b-id => [sha512], :diff => [sha512] }
    nodes/diff -- GET /[sha512]/[sha512] => [sha512]
    nodes/merge -- POST { node_content, patch } => merged node

The Trust Exchange
------------------

    ratings/show -- GET /[sha512] => { object, rating, topic }  // eg google, 7.3, integrity
    ratings/create -- POST / { object, rating, topic } => sha512 of rating
