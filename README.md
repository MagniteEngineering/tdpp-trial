# tdpp-trial
Turtledove++ Trial

## Goal

The goal of this trial is to run real world traffic through a TURTLEDOVE inspired auction flow to prove its effectiveness and identify any challenges and refine the interfaces between Publisher, Browser, SSP and DSP.

## Planned Phases

1. Agree on interest group tagging interface for DSPs
2. Build interest group tagging test page displaying tagged interest groups (and bids) and allowing for manual tagging from page
3. Build auction test page which requests contextual bids using prebid, passes them to iframe and displays all bids (contextual and interest group) along with identifying simple highest bidder.
4. Refine interface for contextual data passed to TURTLEDOVE++ via prebid contextual responses
5. Agree on reporting events that should be fired for this tests
6. Add reporting into test page
7. Update (or create new) test page that chooses and renders a winning ad
8. Iterate on test setup until participants agree its ready for real traffic
9. Agree on spec for a prebid module that facilitates publishers running a subset of traffic through TURTLEDOVE++ trial
10. Build prebid module
11. Run trial through some real world traffic

## Future Phases

There are additional aspects of TURTLEDOVE style auctions that are needed that we should tackle after an initial trial.

* Integrate privacy preserving reporting functionality into this trial
