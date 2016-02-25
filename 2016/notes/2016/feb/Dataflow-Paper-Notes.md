# My Notes on the Dataflow Paper

##### What results are being computed.
– Where in event time they are being computed.
– When in processing time they are materialized.
– How earlier results relate to later refinements.

##### Time Domains
When processing data which relate to events in time, there are two inherent domains of time to consider. Though captured in various places across the 
literature (particularly time management [28] and semantic models [9], but also windowing [22], out-of-order processing [23], punctuations
[30], heartbeats [21], watermarks [2], frames [31]), the detailed examples in section 2.3 will be easier to follow with the concepts 
clearly in mind. The two domains of interest are:

• Event Time, which is the time at which the event itself actually occurred, i.e. a record of system clock time (for whatever system generated the event) at the
time of occurrence.

• Processing Time, which is the time at which an event is observed at any given point during processing within the pipeline, i.e. the 
current time according to the system clock. Note that we make no assumptions about clock synchronization within a distributed system.


##### Design Principles
Though much of our design was motivated by the realworld experiences detailed in Section 3.3 below, it was also
guided by a core set of principles that we believed our model should embody:

• Never rely on any notion of completeness.
• Be flexible, to accommodate the diversity of known use cases, and those to come in the future.
• Not only make sense, but also add value, in the context of each of the envisioned execution engines.
• Encourage clarity of implementation.
• Support robust analysis of data in the context in which they occurred.
