^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Changelog for package rosbridge_library
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

0.7.1 (2014-12-09)
------------------

0.7.5 (2014-12-26)
------------------

0.7.4 (2014-12-16)
------------------

0.7.3 (2014-12-15)
------------------

0.7.2 (2014-12-15)
------------------
* 0.7.1
* update changelog
* Contributors: Jihoon Lee

0.7.0 (2014-12-02)
------------------
* rewrite of advertise service
* cleanup init function
* matches original call_service
* matches original call_service
* service_request --> reuse of call_service (previously defined)
* stop_service --> unadvertise_service
* service_name --> service
* service_type --> type
* removed service_module
* request_id --> id
* Contributors: Russell Toris

0.7.10 (2015-02-25)
-------------------

0.7.9 (2015-02-24)
------------------

0.7.8 (2015-01-16)
------------------

0.7.7 (2015-01-06)
------------------

0.7.6 (2014-12-26)
------------------
* 0.7.5
* update changelog
* 0.7.4
* changelog updated
* 0.7.3
* changelog updated
* 0.7.2
* changelog updated
* 0.7.1
* update changelog
* 0.7.0
* changelog updated
* rewrite of advertise service
* cleanup init function
* matches original call_service
* matches original call_service
* service_request --> reuse of call_service (previously defined)
* stop_service --> unadvertise_service
* service_name --> service
* service_type --> type
* removed service_module
* request_id --> id
* Contributors: Jihoon Lee, Russell Toris

0.6.8 (2014-11-05)
------------------
* add a lock to calls to load_manifest - apparently, it's not thread safe
  fixes #103 and #108
* Contributors: Nils Berg

0.6.7 (2014-10-22)
------------------
* updated package manifests
* Contributors: Russell Toris

0.6.6 (2014-10-21)
------------------

0.6.5 (2014-10-14)
------------------
* 0.6.4
* update changelog
* modify tests
  less duplicated code, some other changes to (hopefully) improve reliability. Tested locally about 30 times without encountering any failures.
* Change the behavior of MessageHandler.transition()
  Now reflects usage in the tests, i.e. a QueueMessageHandler only needs queue_length to be defined, not throttle_rate.
* 0.6.3
* update change log
* install util python module to fix #128
* Contributors: Jihoon Lee, Nils Berg

0.6.4 (2014-10-08)
------------------

0.6.3 (2014-10-07)
------------------
* install util python module to fix `#128 <https://github.com/RobotWebTools/rosbridge_suite/issues/128>`_
* Contributors: Jihoon Lee

0.6.2 (2014-10-06)
------------------
* Remove unused json imports; move json imports to utility
  Fixes #7
* Contributors: Graeme Yeates

0.6.1 (2014-09-01)
------------------
* Handle float infinity and NAN s
* Windows-related fix for PIL Image module import
* Fixed typo in raising type errors.
* something messed up indentation
  not sure how that could happen, worked here.
* map Inf and NaN to null
  JSON does not support Inf and NaN values. Currently they are just written into the JSON and JSON.parse on the client side will fail. Correct is to map them to null which will then be parsed correctly by JSON.parse on the client side.
  The issue with that is that the shortcut for lists of floats might be impossible (maybe someone else with more experience in python comes up with something else?). Maybe something similar is necessary in the to_inst case, but I can not really test them.
  Real world application is to process laser scans, they contain inf and nan values for some drivers if the measurements are invalid or out of range.
* Update .travis.yml and package.xml for rosbridge_library tests
* Put back unregister for the publisher and clarify the reconnect behavior
  of the test case. The exponential backoff of the client causes hard to
  understand timing of the events.
  All specs passed locally on hydro:
  SUMMARY
  * RESULT: SUCCESS
  * TESTS: 103
  * ERRORS: 0
  * FAILURES: 0
* Add copyright notice to the file
* Remove extra whitespace
* Make the test more deterministic
* Remove circular dependency.
* Contributors: Achim Königs, Alex Sorokin, Alexander Sorokin, Jonathan Wade, jon-weisz

0.6.0 (2014-05-23)
------------------
* Ensure that service name is a string
  Closes `#104 <https://github.com/RobotWebTools/rosbridge_suite/issues/104>`_
* Contributors: Piyush Khandelwal

0.5.4 (2014-04-17)
------------------
* removing wrong import
* test case for fixed size of uint8 array
* uses regular expresion to match uint8 array and char array.
* logerr when it fails while message_conversion
* Contributors: Jihoon Lee

0.5.3 (2014-03-28)
------------------
* use queue_size for publishers
* Contributors: Jon Binney

0.5.2 (2014-03-14)
------------------
* First attempt adding latching support for topic publishers
* merging changes of groovy-devel into hydro-devel
* adding missing dependency in rosbridge_library `#70 <https://github.com/RobotWebTools/rosbridge_suite/issues/70>`_
* Fixed wrong unicode encoding
* support publishing non-ascii letters
* Added error message on result=False
  When call_service returns False as result, values contains the error message.
* added parameter lookup to rosbridge_tcp.py, modules where those are used, and default parameters to launch file; internal default-values still get used when launch-file does not provide them; internal defaults can be changed within rosbridge_tcp.py
* Merge branch 'experimental_branch' into new_features
* fix handling of partial/multiple/broken json by avoiding to pass nested json (without op-field) to rosbridge.. probably still needs more complex handling of incoming 'broken' json
* nested service not MiRoR related anymore
* added singleton for request-list; allows provider to send service response without specifying module and type, they get looked up when response is received via request_id
* fix for nested service responses - use ros_loader and message_conversion for populating an according instance
* use message_conversion in handle_servie_request
* snapshot for branch to show to genpy devs
* using float64 instead of std_msgs/Float64 lets scripts run fine.. ; next: fix with using std_msgs/Float64 --> need nested data field
* nested srv uses now message_conversion.extract_values
* adapted test scripted to ros_loader; (removed .srv from module_name
* use rosloader for finding service_class
* fixed calculation of fragment_count
* cleanup: files, notes, some code
* added message_field <message_intervall> to allow client to control delay between messages from rosbridge
* added TODO: check if service successfully registered in ros
* ..
* ..
* added description of new opcodes
* tests, comments, description, ..
* tested rosbridge_websocket with new capabilities; websocket test scripts not working yet..; but new caps are working when using rosbridge_websocket and tcp2ws wrapper --> so only testscripts need to be fixed for websockets.
* updated websocket test service server and client script to use websocket
* updated websocket test service server script to use websocket
* added files to test new caps with websocket server
* feierabend.. morgen weiter mit server & client JSON-decoder, see notes
* fixed parsing of incomplete/multiple JSON in incoming buffer; so clients do not need to use an intervall when sending to rosbridge
* only current changes; not yet done..
* code cleanup, not yet finished..; rosbridge logging much cleaner now
* fixed test_server_defragment - recodegit status
* minor
* linuxonandroid
* fixed some parts; ..still better do some redesign for queueing of messages..
* forced tcp_send to use queue and use delay between sends
* blocking behavior for service requests to non-ros; test-scripts use get-ip4 helper function; ..needs a lot cleanup before next steps..
* need to implement server side blocking of multiple requests, to keep implementation of service provider as easy and simple as possible
* not finished
* some changes.. still needs serveral fixes
* unique request_ids
* fixed deserialization of multiple fragments in incoming-data; was caused by too short delay between socket-sends (<0.2 seconds); maybe only temp. fixed
* added fragment sorting to test-client and test-server
* message_size debugging; TODO: sort list of received fragments! ; make sure receive_buffers are big enough for fragment_size + header..
* minor changes
* testing: service server fragmentsizes receive: 1  send: 1; client fragmentsize receive: 1; is working..
* fixed an error that caused service_response to appear quoted as string once too often; should be ok now
* fragmentation basically working; service_server can request fragmented service_calls, service_client can request fragmented responses; fragmentation can be requested by adding fragmentation_size parameter to any message sent to rosbridge
* some code cleanup
* set service_request_timeout back to 60 seconds; had 2s from timeout_tests..
* fixed example: non-ros_service_server.py to use only 1 socket; commented and structured code and comments in test-scripts
* some minor changes: comments, debug-output, ..
* added test script for non-ros_service_client calling service from non-ros_service_server
* added msg and srv files
* fixed (removed) dependency to beginner_tutorials for service_server test-scripts. beginner_tutorials package not needed anymore.
* behaviour on advertising existing service: replace service-provider, similar to ROS-groovy behaviour, see issues..
* behaviour on advertising existing service: replace service-provider, similar to ROS-groovy behaviour, see issues..
* removed obsolete test-scripts
* stop service added
* first working classes: service_server
* should use its own branch: service_server.py;  add initial thoughts and code-base for developing ServiceServer capability
* fixed errors in protocol.py and defragmentation.py
* added test-scripts for defragmentation AND tcp-server
* change json imports to try to use ujson or simplejson
* change json imports to try to use ujson or simplejson; correct log_message to show length of content/data instead of overall length
* fixed variable name in finish()
* Clean up of defragmentation.py.
* add defragmentation capability
* merge with fuerte-devel
* add defragmentation capability
* commented out that problematic unregister line
* Contributors: Brandon Alexander, Jihoon Lee, Julian Cerruti, Kaijen Hsiao, Stefan Profanter, dave, furushchev, fxm-db, ipa-fxm, root, unknown

0.5.1 (2013-10-31)
------------------
* Implement multiple subscriptions to latched topics (fixes `#1 <https://github.com/RobotWebTools/rosbridge_suite/issues/1>`_).
* generate more natural json for service call result
* add result field to service response
* Contributors: Siegfried-A. Gevatter Pujals, Takashi Ogura

0.5.0 (2013-07-17)
------------------
* 0.5.0 preparation for hydro release
* even more missing depends for unit tests
* more missing test packages
* missing depends added when running tests
* rostest now uses devel instead of install
* rostest added to package
* Contributors: Jihoon Lee, Russell Toris

0.4.4 (2013-04-08)
------------------

0.4.3 (2013-04-03 08:24)
------------------------

0.4.2 (2013-04-03 08:12)
------------------------
* eclipse projects removed
* Contributors: Russell Toris

0.4.1 (2013-03-07)
------------------
* adding message generation build dependency
* Contributors: Jihoon Lee

0.4.0 (2013-03-05)
------------------
* removing rostest
* Commenting out rostest
* Update rosbridge_library/package.xml
  removed <test_depend>rospy</test_depend>
* Fixes "'int' is not iterable" bug.
* Adds test_all.test launch file.
* Error fix from wrong package name.
* Moves test package tests into rosbridge_library.
  I learned about NOINSTALL for msg and srv generation in CMakeList.
* Resolves submodule issues.
* Uses only 1 .gitignore to avoid confusion.
* Merge pull request `#15 <https://github.com/RobotWebTools/rosbridge_suite/issues/15>`_ from baalexander/remove_unregister
  Removes buggy unregister call.
* Removes buggy unregister call.
  Fixes Issue `#12 <https://github.com/RobotWebTools/rosbridge_suite/issues/12>`_.
* Adds BSD license header to code files.
  See Issue `#13 <https://github.com/RobotWebTools/rosbridge_suite/issues/13>`_.
* Removing ultrajson from rosbridge.
  If JSON parsing becomes a performance bottle neck, we can readd it.
* Catkinizing rosbridge_library and server.
* PNG compression now creates a square RGB image padded with new-line characters
* Add stack dependencies and rosdeps.
* Collapse directory structure.
* Moved the packages inside a folder called rosbridge
* Initial commit of rosbridge_library
* Contributors: Austin Hendrix, Brandon Alexander, David Gossow, Jihoon Lee, Jonathan Mace, Russell Toris
