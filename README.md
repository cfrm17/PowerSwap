# Power Swap Valuation


The article discusses valuation models for the following products: power financial indices swap contracts (PWR-SWAP), power financial transmission rights contracts (PWRSWAP- FTR), power physical delivery contracts (PWR-PHYS) and power physical transmission contracts (PWR-TR-SPREAD).

All products have similar valuation structure – index swap (or some index basket swap). Two of these products are purely financial while the other two are of physical delivery type.

Trading system stores historical and current levels of various electricity indices and forward prices (in units of Dollar per MWh). All the products in this report have the following payoff structure:

 

Where I1, I2, I3 · · · are various floating indices or fixed prices (possibly adjusted with spreads) and ti is a set of times, each typically an hour-end within the contract period (also called settlement time). N(ti) is the amount of electricity (notional) at time ti (in MWh), typically a constant throughout the whole settlement period. The following instrument types were considered :

PWR-SWAP:

Power Swap (financial) – the two sides exchange a power index for a fixed price, financially.
I1 = Electricity floating index, typically electricity spot price at a certain node on the grid.
I2 = Fixed amount of dollars per MWh.

 

PWR-SWAP-FTR:

Power Swap FTR (Financial Transmission Rights) – the two sides exchange financially two floating indices, typically electricity spot prices in two zones in the grid.
I1 = Electricity floating index.
I2 = Electricity floating index.

 

PWR-PHYS:

Power Physical – physical delivery of electricity. Openlink considers this deal as an exchange of basket of indices (see the discussion on this product in section 1.2).
I1 = Electricity floating index (spot price at point of delivery), with sign determined by the
position taken.

 


PWR-TR-SPREAD:

Power (Physical) Transmission – physical transmission of electricity between two points on the grid (power at POR is transmitted to POD). Again, Openlink views this contract as an exchange of basket of indices (see the discussion on this product in section 1.2).
I1 = Price of transmission.

 


Typical contract periods, for all products, can range from one specified hour up to a whole month, with large flexibility in the contract period’s structure. Besides spreads on the indices, there are various adjustments that could be applied to the contract structure.

These might be additional external fees, different payment schedule conventions, different holiday schedule conventions, volume calculations conventions etc.

Conditional on the delivery of electricity at the contract terms, where I1 is the spot price and I2 is charges payment (like Inbound charges). Thus one has an outstanding position in physical electricity.

The question of how to evaluate such a contract, before maturity, arises. Meaning, what value to attach to the outstanding position in the electricity that you will later sell/buy, in order to evaluate the whole contract before maturity (see https://finpricing.com/lib/EqCallable.html ).

PWR-PHYS contracts are valuated as a swap of basket of indices, evaluating each buy/sell contract separately in the book (no matter of your buy/sell total portfolio strategy). Before maturity, the system treats the outstanding physical leg of the contract as another index (called POWER in the system). Before maturity this index is equal to the spot index at the point of delivery and after delivery the POWER index is set to 0. Thus the system assumes the entire portfolio of physical buy/sell contracts is balanced in terms of physical delivery at settlement time.
