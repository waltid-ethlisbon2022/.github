title W3C Verifiable Credential Exchange via Wallet Connect

participant User
participant SSI Wallet
participant DAPP
participant relay.walletconnect.com
SSI Wallet->relay.walletconnect.com:register(projectId)
DAPP->relay.walletconnect.com:register(projectId)
note over SSI Wallet,relay.walletconnect.com:enc websocket connection established
User->DAPP:Access DAPP (unauthorized)
DAPP->DAPP:showQRCode(EIP155 from DAPP)
User->SSI Wallet:opens SSI Wallet & scan(QR)
SSI Wallet->DAPP:scan(QR)
SSI Wallet->DAPP:chatInvite()
DAPP->SSI Wallet:joinChat()
DAPP->SSI Wallet:chatMessage(ssi:SiopV2Request)
SSI Wallet->User:confirm consent?
User->SSI Wallet:approves consent & shares credentials
SSI Wallet->SSI Wallet:generate Verifiable Presentation
SSI Wallet->DAPP:chatMessage(ssi:SiopV2Response)
DAPP->DAPP:validateVerifiablePresentation()
DAPP->DAPP:grantAccess()
DAPP->DAPP:redirectUser()
