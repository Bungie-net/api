# IMPORTANT NOTES FOR CONTRIBUTORS

## Pull Requests (Please add Issues instead!)

The Swagger files in this project are generated: as a result, if you manually edit the Swagger files your efforts will be lost.  We have to fix our generator rather than accept pull requests to fix the spec on a more permanent basis.  So please, don't worry about editing the spec manually and issuing a pull request.  (if you would still like to do so for other people to use in the interim, that's great: just know that we can't accept your pull request directly for integration)

Instead, file an Issue and provide the following:

* What validator or generator you're using, including it's version number
* Whether the problem you're experiencing is with the v2 spec, v3 spec, or both
* An example showing an incorrect portion of the spec and the correction you'd like to see made

## Spec Fixes and their priority vs. API fixes and Improvements

At the moment, our priority with the Swagger spec is for it to serve as a means to the end of generating our API documentation.  We're extremely pressed for time, and thus for the time being we don't have much time available to work on the spec itself for more general uses.  This is something I'd very much like to improve in the future, but I wanted to make sure you all know in advance that fixing bugs and providing still-missing features in the API itself will take priority over fixing or improving the Swagger spec files for the near future.

We appreciate your input in making it better, but know that the turnaround for spec-related requests will likely be longer than other requests as a result.

Thank you!
