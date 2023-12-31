

# AlgebraFarming


Abstract base contract for Algebra farmings




## Modifiers
### onlyIncentiveMaker


`modifier onlyIncentiveMaker()`  internal







### onlyOwner


`modifier onlyOwner()`  internal







### onlyFarmingCenter


`modifier onlyFarmingCenter()`  internal







### nonReentrant


`modifier nonReentrant()`  internal









## Variables
### contract INonfungiblePositionManager nonfungiblePositionManager immutable

The nonfungible position manager with which this farming contract is compatible

### contract IAlgebraPoolDeployer deployer immutable

The pool deployer

### contract IFarmingCenter farmingCenter 



### mapping(bytes32 &#x3D;&gt; struct AlgebraFarming.Incentive) incentives 

Represents a farming incentive

*Developer note: bytes32 refers to the return value of IncentiveId.compute*
### address incentiveMaker 



### address owner 



### bool isEmergencyWithdrawActivated 

Users can withdraw liquidity without any checks if active.

### mapping(address &#x3D;&gt; mapping(contract IERC20Minimal &#x3D;&gt; uint256)) rewards 

Returns amounts of reward tokens owed to a given address according to the last time all farms were updated

*Developer note: rewards[owner][rewardToken] &#x3D;&gt; uint256*

## Functions
### setIncentiveMaker


`function setIncentiveMaker(address _incentiveMaker) external`  external

Updates the incentive maker



| Name | Type | Description |
| ---- | ---- | ----------- |
| _incentiveMaker | address | The new incentive maker address |


### setOwner


`function setOwner(address _owner) external`  external

Updates the owner address



| Name | Type | Description |
| ---- | ---- | ----------- |
| _owner | address |  |


### setFarmingCenterAddress


`function setFarmingCenterAddress(address _farmingCenter) external`  external

Updates farming center address



| Name | Type | Description |
| ---- | ---- | ----------- |
| _farmingCenter | address | The new farming center contract address |


### setEmergencyWithdrawStatus


`function setEmergencyWithdrawStatus(bool newStatus) external`  external

Changes &#x60;isEmergencyWithdrawActivated&#x60;. Users can withdraw liquidity without any checks if activated.
User cannot enter to farmings if activated.
_Must_ only be used in emergency situations. Farmings may be unusable after activation.
*Developer note: only owner*



| Name | Type | Description |
| ---- | ---- | ----------- |
| newStatus | bool | The new status of &#x60;isEmergencyWithdrawActivated&#x60;. |


### claimReward


`function claimReward(contract IERC20Minimal rewardToken, address to, uint256 amountRequested) external returns (uint256 reward)`  external

Transfers &#x60;amountRequested&#x60; of accrued &#x60;rewardToken&#x60; rewards from the contract to the recipient &#x60;to&#x60;



| Name | Type | Description |
| ---- | ---- | ----------- |
| rewardToken | contract IERC20Minimal | The token being distributed as a reward |
| to | address | The address where claimed rewards will be sent to |
| amountRequested | uint256 | The amount of reward tokens to claim. Claims entire reward amount if set to 0. |

**Returns:**

| Name | Type | Description |
| ---- | ---- | ----------- |
| reward | uint256 | The amount of reward tokens claimed |

### claimRewardFrom


`function claimRewardFrom(contract IERC20Minimal rewardToken, address from, address to, uint256 amountRequested) external returns (uint256 reward)`  external

Transfers &#x60;amountRequested&#x60; of accrued &#x60;rewardToken&#x60; rewards from the contract to the recipient &#x60;to&#x60;
only for FarmingCenter



| Name | Type | Description |
| ---- | ---- | ----------- |
| rewardToken | contract IERC20Minimal | The token being distributed as a reward |
| from | address | The address of position owner |
| to | address | The address where claimed rewards will be sent to |
| amountRequested | uint256 | The amount of reward tokens to claim. Claims entire reward amount if set to 0. |

**Returns:**

| Name | Type | Description |
| ---- | ---- | ----------- |
| reward | uint256 | The amount of reward tokens claimed |




