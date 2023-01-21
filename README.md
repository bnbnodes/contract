
<img src="logo.svg" width="150" />

# BNBNodes Smart Contract
This repo contains the official bnbnodes.io Smart Contract. 

## DEPLOYED AT BNB CHAIN MAINNET
Address: `0xf50b46db152d4e29b45e29557382428622db7871`
Verified on [bscscan.com](https://bscscan.com/address/0xf50b46db152d4e29b45e29557382428622db7871)


# Audit
The following [link](https://github.com/web3audits/audit-bnbnodes) contains the audit by web3audits.
No issues were found. 

# Documentation

## BNBNodes

### MAX_DIRECT_REFERRAL_DEPTH

```solidity
uint8 MAX_DIRECT_REFERRAL_DEPTH
```

Defines how many levels of referrals can go for the Direct Referral Commission (DRC)

### MIN_POOL_AMOUNT

```solidity
uint256 MIN_POOL_AMOUNT
```

Defines Minimum Amount Required in Daily Pool for Payout to be triggered

### CYCLE_LIMIT_ONE

```solidity
uint256 CYCLE_LIMIT_ONE
```

Defines Investment Cycle Limits per User

### CYCLE_LIMIT_TWO

```solidity
uint256 CYCLE_LIMIT_TWO
```

### CYCLE_LIMIT_THREE

```solidity
uint256 CYCLE_LIMIT_THREE
```

### CYCLE_LIMIT_FOUR

```solidity
uint256 CYCLE_LIMIT_FOUR
```

### FIRST_GEN_DRC

```solidity
uint8 FIRST_GEN_DRC
```

Defines percentages for Direct Referral Commission (DRC) levels

### SECOND_GEN_DRC

```solidity
uint8 SECOND_GEN_DRC
```

### THIRD_AND_MORE_GEN_DRC

```solidity
uint8 THIRD_AND_MORE_GEN_DRC
```

### FIRST_GEN_DNRC

```solidity
uint8 FIRST_GEN_DNRC
```

Defines percentages for Daily Node Reward Commission (DNRC) levels

### SECOND_TO_5TH_GEN_DNRC

```solidity
uint8 SECOND_TO_5TH_GEN_DNRC
```

### SIXTH_TO_10TH_GEN_DNRC

```solidity
uint8 SIXTH_TO_10TH_GEN_DNRC
```

### ELEVENTH_TO_15TH_GEN_DNRC

```solidity
uint8 ELEVENTH_TO_15TH_GEN_DNRC
```

### SIXTEENTH_TO_20TH_GEN_DNRC

```solidity
uint8 SIXTEENTH_TO_20TH_GEN_DNRC
```

### MAX_DAILY_NODE_REWARDS_COMMISSION_DEPTH

```solidity
uint8 MAX_DAILY_NODE_REWARDS_COMMISSION_DEPTH
```

Defines how many levels of rewards comission are distributed

### DAILY_NODE_REWARD_PERCENTAGE

```solidity
uint8 DAILY_NODE_REWARD_PERCENTAGE
```

Defines how many percent (%) Daily Node Reward (DNR) are paid

### HOUSE_FEE_PERCENTAGE

```solidity
uint8 HOUSE_FEE_PERCENTAGE
```

Defines how many percent (%) of new investments are dispersed to the masterAccount

### DAILY_TOP_SPONSOR_POOL_DISTRIBUTION_PERCENT

```solidity
uint8 DAILY_TOP_SPONSOR_POOL_DISTRIBUTION_PERCENT
```

Defines how many percent (%) of the Daily Top Sponsor (DTS) Pool are distributed to Top Sponsors

### DAILY_TOP_SPONSOR_POOL_PERCENT

```solidity
uint8 DAILY_TOP_SPONSOR_POOL_PERCENT
```

Defines how many percent (%) of new investments are flowing into the Daily Pool

### WHALEPOOL_PERCENTAGE_X10

```solidity
uint8 WHALEPOOL_PERCENTAGE_X10
```

Defines how many percent (%) of new investments are flowing into the Whale Pool

### WHALE_RANK_AMOUNT

```solidity
uint256 WHALE_RANK_AMOUNT
```

Defines the amount an investor needs to invest to be considered a whale.

### DAILY_ROUND_DURATION

```solidity
uint256 DAILY_ROUND_DURATION
```

Defines the duration of one round, which is 1 day, equalling 24 hours

### MIN_INVEST

```solidity
uint256 MIN_INVEST
```

Defines the minimum investment amount

### DailyRound

```solidity
struct DailyRound {
  uint256 startTime;
  uint256 endTime;
  bool ended;
  uint256 pool;
  uint256 whalepool;
}
```

### User

```solidity
struct User {
  address account;
  uint256 id;
  struct BNBNodes.Investment investment;
  uint256 referralCount;
  address referrer;
  bool isWhale;
  struct BNBNodes.statistics stats;
  uint256 totalEarnings;
  string rank;
}
```

### Investment

```solidity
struct Investment {
  uint256 totalInvestment;
  uint256 currInvestment;
  uint256 initialInvestment;
  uint256 currInvestmentCycle;
  uint256 currInvestmentDepositTime;
  uint256 currInvestmentWithdrawn;
  uint256 incomeLimitLeft;
  uint256 incomeWithdrawn;
  uint256 directReferralCommission;
  uint256 dailyNodeRewardCommission;
  uint256 dailyTopSponsorBonus;
  uint256 dailyWhaleBonus;
}
```

### statistics

```solidity
struct statistics {
  uint256 totalDirectReferralCommission;
  uint256 totalDailyNodeRewardCommission;
  uint256 totalDailyTopSponsorBonus;
  uint256 totalDailyWhaleBonus;
}
```

### UserDailyRounds

```solidity
struct UserDailyRounds {
  uint256 volume;
}
```

### DTSLeader

```solidity
struct DTSLeader {
  uint256 _amount;
  address _address;
}
```

### topSponsors

```solidity
struct BNBNodes.DTSLeader[4] topSponsors
```

Arrays tracking the Accounts for the Daily Top Sponsor Bonus

### lastTopSponsors

```solidity
struct BNBNodes.DTSLeader[4] lastTopSponsors
```

### lastTopSponsorsWinningAmount

```solidity
uint256[4] lastTopSponsorsWinningAmount
```

### whales

```solidity
address[] whales
```

_address @notice Array tracking whale a_address

### totalWithdrawals

```solidity
uint256 totalWithdrawals
```

Contract-wide Storage variables

### roundID

```solidity
uint256 roundID
```

### currentUserID

```solidity
uint256 currentUserID
```

### masterAccount

```solidity
address masterAccount
```

### userVolPerRound

```solidity
mapping(address => mapping(uint256 => struct BNBNodes.UserDailyRounds)) userVolPerRound
```

Mapping of a unit256 key to the roundID pointing at a UserDailyRounds struct containing the ether volume per *round*

### dailyRounds

```solidity
mapping(uint256 => struct BNBNodes.DailyRound) dailyRounds
```

### addressMap

```solidity
mapping(uint256 => address) addressMap
```

### userMap

```solidity
mapping(address => struct BNBNodes.User) userMap
```

### registerNewUserEvent

```solidity
event registerNewUserEvent(address _userAddress, address _referrer, uint256 _timestamp)
```

### investmentEvent

```solidity
event investmentEvent(address _investorAddr, uint256 _currInvestmentCycle, uint256 _amount, uint256 _timestamp)
```

### directReferralCommissionEvent

```solidity
event directReferralCommissionEvent(address _userAddress, address _referrer, uint256 amount, uint256 _timestamp)
```

### dailyNodeRewardCommissionEvent

```solidity
event dailyNodeRewardCommissionEvent(address _userAddress, address _referrer, uint256 amount, uint256 _timestamp)
```

### withdrawalEvent

```solidity
event withdrawalEvent(address _userAddress, uint256 _amount, uint256 _timestamp)
```

### dailyTopSponsorBonusEvent

```solidity
event dailyTopSponsorBonusEvent(address _userAddress, uint256 _amount, uint256 _timestamp)
```

### dailyWhaleBonusEvent

```solidity
event dailyWhaleBonusEvent(address _userAddress, uint256 _amount, uint256 _timestamp)
```

### newMasterAccountEvent

```solidity
event newMasterAccountEvent(address _oldMasterAccount, address _newMasterAccount, uint256 _timestamp)
```

### constructor

```solidity
constructor(address _owner, address _masterAccount) public
```

Constructor of BNBNodes

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| _owner | address | of the contract |
| _masterAccount | address | account receiving houseFee |

### registerUser

```solidity
function registerUser(uint256 _referrerID) public payable
```

main register function for pay ins

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| _referrerID | uint256 | User.id of who referred the new user |

### setNewMasterAccount

```solidity
function setNewMasterAccount(address _address) external
```

can be used to set a new address as the masterAccount receiving the houseFee

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| _address | address | the address of the new masterAccount |

### startNextRoundAsOwner

```solidity
function startNextRoundAsOwner() external
```

safely callable by contract owner to start new daily round

### forceStartNextRoundAsOwner

```solidity
function forceStartNextRoundAsOwner() external
```

only called in emergencies to force-start new rounds

### getDailyNodeReward

```solidity
function getDailyNodeReward(address _investorAddr) external view returns (uint256 _dailyNodeReward)
```

function that returns the Daily Node Reward (DNR), which is 1% daily of currInvestment, until 300% reached

_called by view (getUnclaimedEarningsbyAddress) or by withdrawEarnings()_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| _investorAddr | address | the investor's address for which DNR wille calculated and returned |

### withdrawEarnings

```solidity
function withdrawEarnings() public
```

withdrawal function called by registered users to receive their payout

_nonReentrant protects from re-entrancy attacks_

### getUnclaimedEarningsByAddress

```solidity
function getUnclaimedEarningsByAddress(address _investorAddress) public view returns (uint256 _amount)
```

_view returns unclaimed earnings of address_

### getRank

```solidity
function getRank(uint256 _amount) external pure returns (string)
```

_memory call returning rank associated to investment amount_

### getIncomeLimitLeft

```solidity
function getIncomeLimitLeft(address _investorAddr) external view returns (uint256 _incomeLimitLeft)
```

_view returning the income limit left of address_

### getRankOf

```solidity
function getRankOf(address _investorAddr) external view returns (string)
```

_view returning rank of specific investor_

### getWhaleCount

```solidity
function getWhaleCount() external view returns (uint256 size)
```

_view returning amount of whales_

### getCurrentInvestmentCycle

```solidity
function getCurrentInvestmentCycle(address _investorAddr) external view returns (uint256 _CurrInvestmentCycle)
```

_view returning current investment cycle_

### getAddressByID

```solidity
function getAddressByID(uint256 _id) public view returns (address _address)
```

_view returning address associated to ID_

### getIDByAddress

```solidity
function getIDByAddress(address _address) public view returns (uint256 _id)
```

_view returning ID associated to address_

### getStatsOfPartners

```solidity
function getStatsOfPartners(address _address) public view returns (uint256 _referralCount, uint256 _activeNodes)
```

_returns (a) direct partners / sponsors (referralcount) and
returns (b) active nodes of direct partners / sponsors (sum of currinvest divided by cost per node of all partners)_

### getROI

```solidity
function getROI(address _address) public view returns (int256 _roiPercentage)
```

_returns the Return On Investment (RoI)
ratio of incomeLimitLeft minus claimable to 3 * currInvest
max return 300%_

### getUnclaimedEarningsByRef

```solidity
function getUnclaimedEarningsByRef(uint256 _id) public view returns (uint256 _amount)
```

