scum AKA mapspec*
================

source cascade update management

At my job I manage the data and design of web maps, and for an upcoming research assignment I will be doing academic writing again. SCUM is an exploration of whether a single abstracted paradigm can be applied to both domains (and hopefully many others too) to monitor and manage the update process.

What does update mean here?
---------------------------

Web maps are the result of data, data query operations, styling rules, and a compilation/rendering/serving process. This process can be described by its source code: the code to create the database and query it, the styling code, and the code to put layers together and instruct the rendering engine what to do with it. Data sources are often updated regularly (for example, Openstreetmap updates continuously), and the source code may be modified over time to make changes to the map or add new features.

What differentiates this from standard source control management is that the input data may be modified to create new features for the map. For example, when OSM data is read into a spatial database, in addition to directly rendering the contents of the resulting tables, we may need to create new features (new tables in the database) for the purposes of the map. This, too, can be described with source code in most cases (e.g. the SQL statements which produce the new tables from the source tables). When an update of the source data occurs, these steps need to be repeated based on the new incoming data. Thus, we may speak of a cascade of updates which will need to be propagated through our source tree of the map -- and which will thus need to be managed.

The same applies, I think, to iterative writing based on changing/derived data, possibly with external input from other literature and/or primary data, leading to multiple outputs through a markup/rendering process\*\*. I would like to create tools which will allow me to experiment with more iterative, atomic writing. This means seperating the final outputs (formatted articles, presentations, web pages) from the raw material (my writing which is version controlled at a fine-grained division such as paragraphs), and from the markup rules which will produce different outputs.

Abstracting the cascading update process
----------------------------------------

The two cases can be mapped onto each other as follows:

MAPS

data source     ->      data stores     ->      styling rules       ->      map compilations

TEXT

(data source)   ->      raw text        ->      text markup rules   ->      formatted output

The principle is that there are multiple outputs possible from a given dataset. Once these have been established, we want a way to keep track of which ones we have made so that when the data is modified we can reapply our styling rules to recreate the outputs with the changed inputs. In the case of writing, the data source is optional -- the main use case is to edit the data store extensively (doing th work of writing), but external inputs could be conceived in this model.

A start
-------

That's the basics. I'm going to explore this model here with more description and eventually code as well.

\* Mapspec is the name for the planned software implementation of this paradigm.

\*\* I believe managing a large writing project in versioned plain text and using tools like Latex or Pandoc to style them with plain text markup is the best way to go.
