# Engineering Planning 3/5/2018

## Moderator/Notetaker: Yondon Fu

### Protocol
**Last Week**
* Support external audit - received initial weekly report and went through the read out with ToB (Yondon/Eric)
* Improve test coverage to 100% - improved branch coverage a good amount, not at 100% due to quirks of coverage tool used, but at a good place right now until audit completes (Yondon)
* Improve protocol documentation - received some helpful feedback from ToB on where to add some clarifying documentation, but did not get to actual writing. Holding off on this until audit completes to prioritize other engineering tasks (Yondon)
* Verification strategy - discussed briefly, but there are not any immediate actionable items until we re-focus on this area (Josh)

**This Week**
* Support external audit (Yondon)
* Document potential change to use a provided broadcaster address instead of a job creator's address when creating a job in an issue (Yondon)

### Go Client
**Last Week**
* ETH client related bug fixes (Yondon)
* Eric will coordinate network protocol changes - there needs to be more security analysis and threat modeling here, but the consensus is that what we have right now is ok and we can do more thorough analysis at a later point once we consider other changes (Eric)
* Eric to document how basicnet works today (Eric)
* Basicnet analysis, documentation. Hope to fix bugs as we go along. Develop a plan for the basicnet, in the short and medium term. (Josh)
* Merge transcoder PR (Josh)
* New release version of go-livepeer node (Eric)

**This Week**
* Goal: improve stability for the end-to-end system (broadcast -> transcode -> validate -> slash, round progression)
* Start implementation for proposed basicnet change (Josh)
* Discuss delayed broadcasting proposal - https://github.com/livepeer/go-livepeer/issues/316 - this is not urgent, but the issue is there to solicit feedback this week (Everyone)
* Transcoder node stability bug fixes to try to prevent crashes as much as possible (Yondon)
    - Panic fd - https://github.com/livepeer/go-livepeer/issues/289
    - Transcoder as broadcaster does work but no one knows streamIDs - https://github.com/livepeer/go-livepeer/issues/284
    - Log ETH tx for debugging - https://github.com/livepeer/go-livepeer/issues/271
    - Node crash due to concurrent map read/write - https://github.com/livepeer/go-livepeer/issues/246
    - Maintain transcoder state (this is probably least priority this week since it is not just a bug fix and is a feature to recover from crashes or going offline) - https://github.com/livepeer/go-livepeer/issues/269
* Issue clean up for go-livepeer to close issues known to be fixed already (Yondon)
* Stability for the verification computation solver, the daemon sometimes crashes (Yondon)

### Protocol Explorer
Overall, was very ambitious. Wrote a ton of code and made good progress on most tasks, but didn’t really finish any. There were are a lot of architectural patterns and refactoring I realized would be necessary groundwork for the tasked enhancements, so I focused on those. (Josiah)

**Last Week**
* Not started
    - Chroma: Video Player - Playlist Selection (ABR)
    - Update ETH faucet button
* Done
    - Form handling patterns (react-final-form)
    - Tracking Global unsubmitted transaction status (TransactionStatusContainer / React Context)
    - Pulling modals from inside view to being their own views (consume TransactionStatusContainer data)
    - Deduplicated a lot of shared code, added updated type annotations (queries, util functions)
    - Added Round type and currentRound query to GraphQL schema
* In-progress Explorer enhancements:
    - Claim Earnings - Button (done) + Transaction Modal
    - Withdraw Stake - Button (done) + Transaction Modal
    - Withdraw Fees - Button (done) + Transaction Modal
    - Add transaction mutations GraphQL schema
    - Transcoder “pending” stats

**This Week**
* Continue Explorer enhancements & deploy (Josiah)
* PRs! Schedule an introduction? - Trying out weekly PR that commits are pushed to throughout the week (Josiah)

### Misc
**Last Week**
* None

**This Week**
* Airdrop mechanism (Doug)
    - Working on messaging and the right way to communicate the process to the community
    - Working on preparing blog post drafts for publishing
    - Working with Josiah on UX
    - Interesting token distribution model to look at for reference is MakerDAO - not straightforward to join the community, but once you overcome the hurdle and technical education, you're welcomed with open arms into a tight knit community with many incentive aligned stakeholders

# Engineering Planning 2/26/2018
### Protocol
**Last Week**
* Truebit collaboration: compile ffmpeg into wasm, set up a repo similar to truebit scrypt repo (Yondon/Josh)
* Improve test coverage to 100% (Yondon)
* Got started on making progress here, but did not complete it
* Update transcoder pool to 20 with 10 active on Rinkeby (Eric) - I’ll do it today (Monday)

**This Week**
* Support external audit (Yondon + Eric)
* Improve test coverage to 100% (Yondon)
* Improve protocol documentation (Yondon)
* Update transcoder pool to 20 with multisig transaction (Eric)

### Go Client
**Last Week**
* Debug transcoder inactivity issue (Eric) - did not finish
* Code review for ffmpeg transcoder PR (Eric)
* Further work on transcoder PR; addressed comments, added tests (Josh)

**This Week**
* Bug fix - Transcoder Round Initialization stops (Yondon)
* Eric will coordinate network protocol changes (Eric)
* Eric to document how basicnet works today (Eric)
* Basicnet analysis, documentation. Hope to fix bugs as we go along. Develop a plan for the basicnet, in the short and medium term. (Josh)
* Merge transcoder PR (Josh)

### Protocol Explorer
**Last Week**
* Feedback for bond task flow (everyone)
* Task flows for Unbond, ClaimEarning, WithdrawStake, WithdrawFee (Josiah)
* Token distribution experience depending on discussions this week, not expected to be fully designed by eow (Josiah)
* Update sdk binding (Eric coordinate with Josiah)

**This Week**
* Education as “work”. Client-validated. How do we begin to create this content?
* Secondary mechanism to “prove humanity” (captcha? Multi-factor? tokens?)
* Chroma: Video Player - Playlist Selection (ABR)
* Prioritize Explorer Enhancements (bold means prioritize for this week)
  * **Claim Earnings - Button + Transaction Modal**
  * **Round Initialization - Navbar Status**
  * **Withdraw Stake - Button + Transaction Modal**
  * **Withdraw Fees - Button + Transaction Modal**
  * Pending Price/Cut/Fees
  * Update ETH Faucet (external link)
  * Messaging - Coaches
  * Messaging - Info Icons + Explanatory Modals
  * Claim Earnings - Badge
  * Claim Earnings - Warning Modal
  * Round Initialization - Warning Modal
* Website redesign (Eric make sure to get asset from Brad)


### Misc
**Last Week**
* Public testnet deployment (Eric)
* Design feedback - deadline on Wednesday (Everyone)
* Token Distribution - feedback by Thursday morning (please review the email thread)
* Community call this week (Doug)
* Audit Instructions (Doug)
* Create actionable items from the ETHDenver recap, and capture in Github. (Doug)

#### Note:
* Validation strategy (Josh)
  * For now, we can go with something naive like comparing frame rates and bit rates, but are many ways to break that, both intentionally and unintentionally. So I think we really need to spend some time developing the metrics we're going to be validating, and incorporate that into our long-term planning. Doubt we'll get this right on the first try, either. Make sure we have flexibility built into the protocol to refine the validation strategy after launch.
* Protocol explorer chores - decided to delay to a later time
  * Pre-commit hooks for linting/formatting
  * CONTRIBUTING.md
  * CI - Testing
  * CI - Coverage
  * CI - Deployment / Publishing
  * CI - Code Quality

# Engineering Planning 2/20/2018
#### Protocol Explorer
* Feedback for bond task flow (everyone)
* Task flows for Unbond, ClaimEarning, WithdrawStake, WithdrawFee (Josiah)
* Token distribution experience depending on discussions this week, not expected to be fully designed by eow (Josiah)
* Update sdk binding (Eric coordinate with Josiah)

#### Protocol
* Truebit collaboration: compile ffmpeg into wasm,  set up a repo similar to truebit scrypt repo (Yondon/Josh)
* Improve test coverage to 100% (Yondon)
* Update transcoder pool to 20 with 10 active on Rinkeby (Eric)

#### Go-Client
* Debug transcoder inactivity issue (Eric)
* Code review for ffmpeg transcoder PR (Eric)

#### Misc
* Public testnet deployment (Eric)
* Design feedback - deadline on Wednesday (Everyone)
* Token Distribution - feedback by Thursday morning (please review the email thread)
* Community call this week (Doug)
* Audit Instructions (Doug)
* Create actionable items from the ETHDenver recap, and capture in Github. (Doug)

# Eng Planning 2/12/2018
### Protocol
* Continue to make progress on the milestone (we should be done before Doug & Yondon leave for Eth Denver)

### Protocol Explorer
* Task flows + wireframes for Claim, Bond, Unbond, ClaimReward (Josiah)

### Go-Client
* Better unit test coverage for transcoding (Josh)
* Final PR for ffmpeg transcoder (Josh)
* Found a cause of the bug in networking (Eric)

### Misc
* Eth Denver getting started guide (Everyone)
* Prep for Truebit collaboration next week (Yondon, Josh, Eric)
* Operations key management (Eric)
* Protocol / testnet deployment (Eric)


# Eng Planning 2/05/2018
### Protocol
Goal: Start external audit on 2/14
* Consensys security checklist (we didn't get to it last week, but got through a lot of other security audit todos) (Doug / Yondon)
* Continue working through issues found through the audit (Yondon)
* Internal security audit checklist (Eric)

### Protocol Explorer
* Wireframe for bonding/unbonding (Josiah)
* Basic bonding interface (Josiah)
* New UI/UX dev process / tools (Josiah)

### Go-Client
* Document new transcoding system so everyone else can learn the different components involved (Josh)
* New transcoder implementation (Josh)

### Misc
* Document [How we work](https://github.com/livepeer/project-management#how-we-work) (Doug)
* Start using [explorer project section](https://github.com/livepeer/livepeerjs/projects/1) to capture tickets for the explorer (Everyone)
* Use [Project Proposals](https://github.com/livepeer/project-management/projects/1) and [Livepeer Community Roadmap](https://github.com/livepeer/project-management/projects/2) to capture high-level thoughts/updates (Everyone)

# Eng Planning 1/29/2018
### Protocol
Goal: Start external audit on 2/14 (operation safe v-day)
* Consensys security checklist (Doug / Yondon)
* User acceptance security audit (Eric)
* Integration tests for user interactions (Yondon)
* Improve unit test coverage (Yondon)

### Protocol Explorer
* Finish transcoder election view (Josiah)
* Documentation for protocol explorer + js sdk (Josiah)

### Go Client
* Testing for segmenter ffmpeg integration (Josh)
* Remove transcoder ffmpeg dependency (Josh)

### Misc
* Ensure testnet uptime during this week's live broadcasts (Eric)


# Eng Planning 1/22/2018
### Protocol
Goal: Start Internal Audit
Action Items:
* 2 last code changes before code freeze for internal audit (Yondon)
  * Transcoding election fix
  * Enforce transcoder bonding
* Sanity checks around Livepeer Verifier (Doug / Yondon)
* Live contract update (Yondon)
* Doug to start internal audit
* Eric to do the checklist version of internal audit

### Protocol Explorer
* Transcoder view design session (Josiah)
* Transcoder view implementation (Josiah)

### Go Client
* ffmpeg project (Josh)
* Integration test plan for go-livepeer and go-livepeer-basicnet (Eric)
* Job assignment fix (Yondon)
* Upgrade IPFS to new version (Yondon Volunteered)

### Misc
* Timescale-accurate testnet protocol deployment (Yondon/Eric)
* Dockerize Livepeer (Joe)
* Auto-gen ABIs pushed to later
* Continuous deployment of web player pushed to later


# Eng Planning 1/16/2018
### Protocol
Goal: Prep for Internal Audit
Action Items:
* Testing - fee distribution, job being distributed to different transcoders, watch / slash, transcoder set rotation (Doug)
* Testing - seeing adaptive bitrate stream (Eric)
* Linter / compiler warnings (Yondon)
* Covergae testing (Yondon)
* Start internal audit this week

### Protocol Explorer
Goal: Continue to make progress on UI/UX
Action Items:
* Demo during community call on 1/18 (Josiah)
* Transcoder view, transcoder election (Josiah)
* Deploy a version to S3 (Josiah)

### Go Client
Goal: Stability
Action Items:
* Remove ffmpeg external dependencies (Josh)
* Bug fixes (Eric)
* Watcher (need a owner)

### MISC
* Currently the node loses all of its state when stopped.  Filed [an issue](https://github.com/livepeer/go-livepeer/issues/269)
* Deploy the test player at a different URL
* Continuous deployment of the web player
* Monitoring endpoint health, auto-restart
* Moving beyond using screen to run Livepeer in AWS
* Make logs available
* Auto-generated ABI repo
* Research integration test tools (Eric)
* Move testnet deploy key management to 1password (Eric)

# Eng Planning 1/8/2018

### Protocol
Goal: Internal Audit
Action Items:
* Simulating genesis state - Yondon
* Upgrade path (version number) - Yondon
* Internal audit checklist - Doug

### Protocol Explorer
* Profile view - Josiah
* Transcoder view - Josiah
* Deployment to S3 - Josiah

### Go Client
* Duplicate nonce bug - Yondon
* Standard SDK spec (golang and js sdk should have the same interface) - Yondon/Josiah
* Memory issue - Eric
* Error messages - Eric
* Bug squash - Eric

### Misc
* Ops - roles for different environments, key storage, etc (Eric to work with Joe offline)
* Protocol explorer next step: bond/unbond/deposit/withdraw/claim
* Video player next step: add resolution picker
* Go client next step: Eric to work on Jan release goal
* Postpone public testnet deployment until later time
