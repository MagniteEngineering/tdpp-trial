# Initial Prototype Flow

The intention is to mimic a simplified TURTLEDOVE flow then iterate to add features and restrict functionality to reach a workable privacy-safe solution

1. User visits webpage indicating their affinity for a given interest and are tagged into an interest group using the interest group tagging interface. 
    * Tagging is performed by calling a JS function triggered on the page
    * Tagging parameters can be provided by advertiser, dsp, or other buy side participant.
    * To simplify the flow, relevant ads will also be provided ad interest group tagging time.
2. User visits a publisher webpage where ads are rendered.
3. Prebid.js makes contextual requests for bids to display ads to this user on this page
4. Bids are passed into an iframe which has access to interest groups and cached bids/ads stored in step 1.
5. On browser bidding logic compares cached bids with passed in contextual bids and chooses a winner
6. Winning creative renders within a sub-iframe
