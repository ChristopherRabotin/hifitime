# hifitime 0.0.1

Precise date and time handling in Rust built on top of
[` std::time::Duration`](https://doc.rust-lang.org/std/time/struct.Duration.html).
The Epoch used is TAI Epoch of 01 Jan 1900 at midnight, but that should not matter in
day-to-day use of this library.

Features:

 * [x] Leap seconds (as announced by the IETF on a yearly basis)
 * [x] Julian dates and Modified Julian dates
 * [x] UTC representation with ISO8601 formatting
 * [x] Allows building custom TimeSystem (e.g. Julian days)
 * [x] Time varying `TimeZone`s to represent static or very high speed reference frames (cf. the `tz` test in the `tests` module)

Almost all examples are validated with external references, as detailed on a test-by-test
basis.

*NOTE:* Each time computing library may decide when the extra leap second exists as explained
in the [IETF leap second reference](https://www.ietf.org/timezones/data/leap-seconds.list).
To ease computation, `hifitime` decides that second is the 60th of a UTC date, if such exists.
Note that this second exists at a different time than defined on NASA HEASARC. That tool is
used for validation of Julian dates. As an example of how this is handled, check the Julian
day computations for [2015-06-30 23:59:59](https://goo.gl/o3KXSR),
[2015-06-30 23:59:60](https://goo.gl/QyUyrC) and [2015-07-01 00:00:00](https://goo.gl/Y25hpn).

Does not include:

* [ ] Dates only, or times only (i.e. handles only the combination of both)
* [ ] Custom formatting of date time objects (for now)