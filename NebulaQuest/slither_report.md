**THIS CHECKLIST IS NOT COMPLETE**. Use `--show-ignored-findings` to show all the results.
Summary
 - [uninitialized-local](#uninitialized-local) (1 results) (Medium)
 - [shadowing-local](#shadowing-local) (4 results) (Low)
 - [reentrancy-benign](#reentrancy-benign) (2 results) (Low)
 - [reentrancy-events](#reentrancy-events) (1 results) (Low)
 - [pragma](#pragma) (1 results) (Informational)
 - [naming-convention](#naming-convention) (26 results) (Informational)
 - [unused-state](#unused-state) (1 results) (Informational)
## uninitialized-local
Impact: Medium
Confidence: Medium
 - [ ] ID-0
[NebulaQuest.submitAnswers(uint8,bytes32[]).score](src/NebulaQuest.sol#L105) is a local variable never initialized

src/NebulaQuest.sol#L105


## shadowing-local
Impact: Low
Confidence: High
 - [ ] ID-1
[NebulaEvolution.constructor(string,string,address,address)._symbol](src/NebulaEvolution.sol#L67) shadows:
	- [ERC721._symbol](lib/openzeppelin-contracts/contracts/token/ERC721/ERC721.sol#L26) (state variable)

src/NebulaEvolution.sol#L67


 - [ ] ID-2
[NebulaQuestCoin.constructor(string,string,address,address)._name](src/NebulaQuestCoin.sol#L66) shadows:
	- [EIP712._name](lib/openzeppelin-contracts/contracts/utils/cryptography/EIP712.sol#L49) (state variable)
	- [ERC20._name](lib/openzeppelin-contracts/contracts/token/ERC20/ERC20.sol#L36) (state variable)

src/NebulaQuestCoin.sol#L66


 - [ ] ID-3
[NebulaEvolution.constructor(string,string,address,address)._name](src/NebulaEvolution.sol#L66) shadows:
	- [ERC721._name](lib/openzeppelin-contracts/contracts/token/ERC721/ERC721.sol#L23) (state variable)

src/NebulaEvolution.sol#L66


 - [ ] ID-4
[NebulaQuestCoin.constructor(string,string,address,address)._symbol](src/NebulaQuestCoin.sol#L67) shadows:
	- [ERC20._symbol](lib/openzeppelin-contracts/contracts/token/ERC20/ERC20.sol#L37) (state variable)

src/NebulaQuestCoin.sol#L67


## reentrancy-benign
Impact: Low
Confidence: Medium
 - [ ] ID-5
Reentrancy in [NebulaEvolution.safeMint(address)](src/NebulaEvolution.sol#L90-L123):
	External calls:
	- [_safeMint(_user,tokenId)](src/NebulaEvolution.sol#L121)
		- [retval = IERC721Receiver(to).onERC721Received(operator,from,tokenId,data)](lib/openzeppelin-contracts/contracts/token/ERC721/utils/ERC721Utils.sol#L33-L47)
		- [ERC721Utils.checkOnERC721Received(_msgSender(),address(0),to,tokenId,data)](lib/openzeppelin-contracts/contracts/token/ERC721/ERC721.sol#L315)
	State variables written after the call(s):
	- [_setTokenURI(tokenId,finalURI)](src/NebulaEvolution.sol#L122)
		- [_tokenURIs[tokenId] = _tokenURI](lib/openzeppelin-contracts/contracts/token/ERC721/extensions/ERC721URIStorage.sol#L58)

src/NebulaEvolution.sol#L90-L123


 - [ ] ID-6
Reentrancy in [NebulaQuest._distributeRewards(uint16)](src/NebulaQuest.sol#L148-L165):
	External calls:
	- [i_coin.mint(msg.sender,_score * DECIMALS)](src/NebulaQuest.sol#L149)
	- [nftId = i_nft.safeMint(msg.sender)](src/NebulaQuest.sol#L158)
	State variables written after the call(s):
	- [s_studentInfo[msg.sender] = Student(nftId,certificates)](src/NebulaQuest.sol#L161)

src/NebulaQuest.sol#L148-L165


## reentrancy-events
Impact: Low
Confidence: Medium
 - [ ] ID-7
Reentrancy in [NebulaEvolution.safeMint(address)](src/NebulaEvolution.sol#L90-L123):
	External calls:
	- [_safeMint(_user,tokenId)](src/NebulaEvolution.sol#L121)
		- [retval = IERC721Receiver(to).onERC721Received(operator,from,tokenId,data)](lib/openzeppelin-contracts/contracts/token/ERC721/utils/ERC721Utils.sol#L33-L47)
		- [ERC721Utils.checkOnERC721Received(_msgSender(),address(0),to,tokenId,data)](lib/openzeppelin-contracts/contracts/token/ERC721/ERC721.sol#L315)
	Event emitted after the call(s):
	- [MetadataUpdate(tokenId)](lib/openzeppelin-contracts/contracts/token/ERC721/extensions/ERC721URIStorage.sol#L59)
		- [_setTokenURI(tokenId,finalURI)](src/NebulaEvolution.sol#L122)

src/NebulaEvolution.sol#L90-L123


## pragma
Impact: Informational
Confidence: High
 - [ ] ID-8
2 different versions of Solidity are used:
	- Version constraint ^0.8.20 is used by:
		-[^0.8.20](lib/openzeppelin-contracts/contracts/access/AccessControl.sol#L4)
		-[^0.8.20](lib/openzeppelin-contracts/contracts/access/IAccessControl.sol#L4)
		-[^0.8.20](lib/openzeppelin-contracts/contracts/access/Ownable.sol#L4)
		-[^0.8.20](lib/openzeppelin-contracts/contracts/interfaces/IERC1363.sol#L4)
		-[^0.8.20](lib/openzeppelin-contracts/contracts/interfaces/IERC165.sol#L4)
		-[^0.8.20](lib/openzeppelin-contracts/contracts/interfaces/IERC20.sol#L4)
		-[^0.8.20](lib/openzeppelin-contracts/contracts/interfaces/IERC4906.sol#L4)
		-[^0.8.20](lib/openzeppelin-contracts/contracts/interfaces/IERC5267.sol#L4)
		-[^0.8.20](lib/openzeppelin-contracts/contracts/interfaces/IERC721.sol#L4)
		-[^0.8.20](lib/openzeppelin-contracts/contracts/interfaces/draft-IERC6093.sol#L3)
		-[^0.8.20](lib/openzeppelin-contracts/contracts/token/ERC20/ERC20.sol#L4)
		-[^0.8.20](lib/openzeppelin-contracts/contracts/token/ERC20/IERC20.sol#L4)
		-[^0.8.20](lib/openzeppelin-contracts/contracts/token/ERC20/extensions/ERC20Permit.sol#L4)
		-[^0.8.20](lib/openzeppelin-contracts/contracts/token/ERC20/extensions/IERC20Metadata.sol#L4)
		-[^0.8.20](lib/openzeppelin-contracts/contracts/token/ERC20/extensions/IERC20Permit.sol#L4)
		-[^0.8.20](lib/openzeppelin-contracts/contracts/token/ERC20/utils/SafeERC20.sol#L4)
		-[^0.8.20](lib/openzeppelin-contracts/contracts/token/ERC721/ERC721.sol#L4)
		-[^0.8.20](lib/openzeppelin-contracts/contracts/token/ERC721/IERC721.sol#L4)
		-[^0.8.20](lib/openzeppelin-contracts/contracts/token/ERC721/IERC721Receiver.sol#L4)
		-[^0.8.20](lib/openzeppelin-contracts/contracts/token/ERC721/extensions/ERC721URIStorage.sol#L4)
		-[^0.8.20](lib/openzeppelin-contracts/contracts/token/ERC721/extensions/IERC721Metadata.sol#L4)
		-[^0.8.20](lib/openzeppelin-contracts/contracts/token/ERC721/utils/ERC721Utils.sol#L4)
		-[^0.8.20](lib/openzeppelin-contracts/contracts/utils/Address.sol#L4)
		-[^0.8.20](lib/openzeppelin-contracts/contracts/utils/Base64.sol#L4)
		-[^0.8.20](lib/openzeppelin-contracts/contracts/utils/Context.sol#L4)
		-[^0.8.20](lib/openzeppelin-contracts/contracts/utils/Errors.sol#L4)
		-[^0.8.20](lib/openzeppelin-contracts/contracts/utils/Nonces.sol#L3)
		-[^0.8.20](lib/openzeppelin-contracts/contracts/utils/Panic.sol#L4)
		-[^0.8.20](lib/openzeppelin-contracts/contracts/utils/ReentrancyGuard.sol#L4)
		-[^0.8.20](lib/openzeppelin-contracts/contracts/utils/ShortStrings.sol#L4)
		-[^0.8.20](lib/openzeppelin-contracts/contracts/utils/StorageSlot.sol#L5)
		-[^0.8.20](lib/openzeppelin-contracts/contracts/utils/Strings.sol#L4)
		-[^0.8.20](lib/openzeppelin-contracts/contracts/utils/cryptography/ECDSA.sol#L4)
		-[^0.8.20](lib/openzeppelin-contracts/contracts/utils/cryptography/EIP712.sol#L4)
		-[^0.8.20](lib/openzeppelin-contracts/contracts/utils/cryptography/MessageHashUtils.sol#L4)
		-[^0.8.20](lib/openzeppelin-contracts/contracts/utils/introspection/ERC165.sol#L4)
		-[^0.8.20](lib/openzeppelin-contracts/contracts/utils/introspection/IERC165.sol#L4)
		-[^0.8.20](lib/openzeppelin-contracts/contracts/utils/math/Math.sol#L4)
		-[^0.8.20](lib/openzeppelin-contracts/contracts/utils/math/SafeCast.sol#L5)
		-[^0.8.20](lib/openzeppelin-contracts/contracts/utils/math/SignedMath.sol#L4)
	- Version constraint 0.8.26 is used by:
		-[0.8.26](src/NebulaEvolution.sol#L3)
		-[0.8.26](src/NebulaQuest.sol#L3)
		-[0.8.26](src/NebulaQuestCoin.sol#L3)

lib/openzeppelin-contracts/contracts/access/AccessControl.sol#L4


## naming-convention
Impact: Informational
Confidence: High
 - [ ] ID-9
Event [NebulaQuest.NebulaQuest_ExamFailed(address,uint8,uint16)](src/NebulaQuest.sol#L71) is not in CapWords

src/NebulaQuest.sol#L71


 - [ ] ID-10
Parameter [NebulaEvolution.levelsSetter(uint256,uint256)._level](src/NebulaEvolution.sol#L153) is not in mixedCase

src/NebulaEvolution.sol#L153


 - [ ] ID-11
Variable [NebulaQuest.i_nft](src/NebulaQuest.sol#L43) is not in mixedCase

src/NebulaQuest.sol#L43


 - [ ] ID-12
Event [NebulaEvolution.NebulaEvolution_LevelUpdated(uint256,uint256)](src/NebulaEvolution.sol#L54) is not in CapWords

src/NebulaEvolution.sol#L54


 - [ ] ID-13
Parameter [NebulaEvolution.safeMint(address)._user](src/NebulaEvolution.sol#L90) is not in mixedCase

src/NebulaEvolution.sol#L90


 - [ ] ID-14
Event [NebulaEvolution.NebulaEvolution_TheGasIsFreezingABirthIsOnTheWay(uint256)](src/NebulaEvolution.sol#L52) is not in CapWords

src/NebulaEvolution.sol#L52


 - [ ] ID-15
Parameter [NebulaEvolution.updateNFT(uint256,uint256)._exp](src/NebulaEvolution.sol#L131) is not in mixedCase

src/NebulaEvolution.sol#L131


 - [ ] ID-16
Parameter [NebulaQuest.submitAnswers(uint8,bytes32[])._encryptedAnswers](src/NebulaQuest.sol#L99) is not in mixedCase

src/NebulaQuest.sol#L99


 - [ ] ID-17
Event [NebulaQuest.NebulaQuest_AnswersUpdated(uint8)](src/NebulaQuest.sol#L73) is not in CapWords

src/NebulaQuest.sol#L73


 - [ ] ID-18
Variable [NebulaEvolution.s_expPerLevel](src/NebulaEvolution.sol#L46) is not in mixedCase

src/NebulaEvolution.sol#L46


 - [ ] ID-19
Parameter [NebulaQuestCoin.burn(uint256)._amount](src/NebulaQuestCoin.sol#L100) is not in mixedCase

src/NebulaQuestCoin.sol#L100


 - [ ] ID-20
Event [NebulaQuestCoin.NebulaQuestCoin_TokenBurned(uint256)](src/NebulaQuestCoin.sol#L45) is not in CapWords

src/NebulaQuestCoin.sol#L45


 - [ ] ID-21
Parameter [NebulaEvolution.levelsSetter(uint256,uint256)._amountOfExp](src/NebulaEvolution.sol#L153) is not in mixedCase

src/NebulaEvolution.sol#L153


 - [ ] ID-22
Parameter [NebulaQuestCoin.mint(address,uint256)._amount](src/NebulaQuestCoin.sol#L89) is not in mixedCase

src/NebulaQuestCoin.sol#L89


 - [ ] ID-23
Event [NebulaEvolution.NebulaEvolution_NFTUpdated(uint256,string)](src/NebulaEvolution.sol#L56) is not in CapWords

src/NebulaEvolution.sol#L56


 - [ ] ID-24
Parameter [NebulaQuest.getStudentInfo(address)._student](src/NebulaQuest.sol#L168) is not in mixedCase

src/NebulaQuest.sol#L168


 - [ ] ID-25
Variable [NebulaEvolution.s_starInformation](src/NebulaEvolution.sol#L48) is not in mixedCase

src/NebulaEvolution.sol#L48


 - [ ] ID-26
Event [NebulaQuest.NebulaQuest_ExamPassed(address,uint8,uint16)](src/NebulaQuest.sol#L69) is not in CapWords

src/NebulaQuest.sol#L69


 - [ ] ID-27
Parameter [NebulaQuest.answerSetter(uint8,bytes32[])._correctAnswers](src/NebulaQuest.sol#L131) is not in mixedCase

src/NebulaQuest.sol#L131


 - [ ] ID-28
Variable [NebulaQuest.i_coin](src/NebulaQuest.sol#L42) is not in mixedCase

src/NebulaQuest.sol#L42


 - [ ] ID-29
Parameter [NebulaQuest.answerSetter(uint8,bytes32[])._examIndex](src/NebulaQuest.sol#L131) is not in mixedCase

src/NebulaQuest.sol#L131


 - [ ] ID-30
Event [NebulaQuestCoin.NebulaQuestCoin_TokenMinted(address,uint256)](src/NebulaQuestCoin.sol#L43) is not in CapWords

src/NebulaQuestCoin.sol#L43


 - [ ] ID-31
Variable [NebulaQuest.s_studentsScore](src/NebulaQuest.sol#L63) is not in mixedCase

src/NebulaQuest.sol#L63


 - [ ] ID-32
Parameter [NebulaQuestCoin.mint(address,uint256)._to](src/NebulaQuestCoin.sol#L89) is not in mixedCase

src/NebulaQuestCoin.sol#L89


 - [ ] ID-33
Parameter [NebulaQuest.submitAnswers(uint8,bytes32[])._examIndex](src/NebulaQuest.sol#L99) is not in mixedCase

src/NebulaQuest.sol#L99


 - [ ] ID-34
Parameter [NebulaEvolution.updateNFT(uint256,uint256)._tokenId](src/NebulaEvolution.sol#L131) is not in mixedCase

src/NebulaEvolution.sol#L131


## unused-state
Impact: Informational
Confidence: High
 - [ ] ID-35
[NebulaQuest.MAX_SCORE](src/NebulaQuest.sol#L49) is never used in [NebulaQuest](src/NebulaQuest.sol#L28-L173)

src/NebulaQuest.sol#L49


