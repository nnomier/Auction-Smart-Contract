# PRIVATE AUCTION 

A music producer would like to set up an auction to sell a recording exclusively in advance. The winner of the auction is the highest bidder, but only pays the second highest price.



The smart contract is written in solidity.

## Assumptions:

**General:**

- All values are sent and calculated in wei.

- Deposits sent by the manager or the participants have to be >= 0.001 ether.

- A mapping “bids” maps each participant to their commitment, deposit value, a Boolean stating whether or not they already made a bid, the value to be returned at the end ( is always equal to zero before revealing time) and a Boolean stating whether or not he’s honest.

  

**Constructor :**

Bidding time , Revealing time and Finalization time are all initialized in days.

The caller of the constructor is the auction manager.

**Bidding:**

Each participant can only bid once.

The manager can’t make a bid.

**Revealing:**

The value the bidder pays here must be (valueCommited - deposit)Hash(P || Value || nonce) must be equal to the original commitment.

Highest bid and second highest bid are updated.

**Finalization:**

**Finalize by manager:**

The winner is sent the difference between his bid and the second highest bid.

Each participant receives his bid back.

The manager receives the second highest bid as the price for the record.

The deposits paid by cheaters are transferred to the manager.


**Finalize by a participant:**

This function is called when the finalization time is over and the manager didn’t end the auction.

This function can only be called by one participant.

The person who called the function gets half of the manager’s deposit.

A ratio of the deposits paid by cheaters are transferred to each participant.
