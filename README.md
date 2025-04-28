# ECSR-API-Docs
Swagger UI Documentation for ECSR.io API

## Raw Docs:
Swagger UI Site is Coming Soon!

I will also improve these Raw Docs later on since the formatting kinda sucks.

### Account Information
getUserRobloxBadges GET
https://ecsr.io/apisite/accountinformation/v1/users/2828/roblox-badges

setUserDescription POST
description: newDescription
https://ecsr.io/apisite/accountinformation/v1/description

### Account Settings
getMyEmail GET
https://ecsr.io/apisite/accountsettings/v1/email

getInventoryPrivacy GET
https://ecsr.io/apisite/accountsettings/v1/inventory-privacy

setInventoryPrivacy POST
inventoryPrivacy: newPrivacy
https://ecsr.io/apisite/accountsettings/v1/inventory-privacy

getTradePrivacy GET
https://ecsr.io/apisite/accountsettings/v1/trade-privacy

setTradePrivacy POST
tradePrivacy: newPrivacy
https://ecsr.io/apisite/accountsettings/v1/trade-privacy

getTradeValue GET
https://ecsr.io/apisite/accountsettings/v1/trade-value

setTradeValue POST
tradeValue: newValue
https://ecsr.io/apisite/accountsettings/v1/trade-value

### Ads
uploadAdvertisement POST
formData: {"name": name, "files": file}
https://ecsr.io/apisite/ads/v1/user-ads/{Type}/create?assetId={targetId}

getAds GET
https://ecsr.io/apisite/ads/v1/user-ads/{creatorType: User, Group}/{creatorId}

bidOnAd POST
robux
https://ecsr.io/apisite/ads/v1/user-ads/{adId}/run

### API
getAlert GET
https://ecsr.io/apisite/api/alerts/alert-info

### Auth
login POST
ctype: 'username'
cvalue: username
password
https://ecsr.io/apisite/auth/v2/login

logout POST
https://ecsr.io/apisite/auth/v2/logout

changePassword POST
currentPassword: existingPassword
newPassword
https://ecsr.io/apisite/auth/v2/user/passwords/change

validateUsername GET
https://ecsr.io/apisite/auth/v1/usernames/validate?username={username}&context={context}

changeUsername POST
username
password
https://ecsr.io/apisite/auth/v1/username

logoutFromAllOtherSessions POST
https://ecsr.io/apisite/auth/v2/logoutfromallsessionsandreauthenticate

### Avatar
getRules GET
https://ecsr.io/apisite/avatar/v1/avatar-rules

getAvatar GET
https://ecsr.io/apisite/avatar/v1/users/{userId}/avatar

getMyAvatar GET
https://ecsr.io/apisite/avatar/v1/avatar

redrawMyAvatar POST
https://ecsr.io/apisite/avatar/v1/avatar/redraw-thumbnail

setWearingAssets POST
assetIds
https://ecsr.io/apisite/avatar/v1/avatar/v1/avatar/set-wearing-assets

setColors POST
bodyColors
https://ecsr.io/apisite/avatar/v1/avatar/v1/avatar/set-body-colors

getOutfits GET
https://ecsr.io/apisite/avatar/v1/users/{userId}/outfits?itemsPerPage=50&page=1

createOutfit POST
name
https://ecsr.io/apisite/avatar/v1/outfits/create

wearOutfit POST
https://ecsr.io/apisite/avatar/v1/outfits/{outfitId}/wear

deleteOutfit POST
https://ecsr.io/apisite/avatar/v1/outfits/{outfitId}/delete

renameOutfit PATCH
name
https://ecsr.io/apisite/avatar/v1/outfits/{outfitId}

### Catalog
searchCatalog GET
https://ecsr.io/apisite/catalog/v1/search/items?category={category}&limit={limit}&sortType={sort}
optional: &cursor={cursor}, &keyword={keyword}, &subcategory={subcategory}, &creatorTargetId={creatorId}&&creatorType={creatorType}

getProductInfoLegacy GET
Note: This API is meant for server-side requests. It may be a hidden API.
https://ecsr.io/apisite/api/marketplace/productinfo?assetId={assetId}

getItemDetails POST
itemType: 'Asset'
id: v
https://ecsr.io/apisite/catalog/v1/catalog/items/details

getRecommendations GET
https://ecsr.io/apisite/catalog/v1/recommendations/asset/{assetTypeId}?contextAssetId={assetId}&numItems={limit}

getComments GET
https://ecsr.io/comments/get-json?assetId={assetId}&startIndex={offset}&thumbnailWidth=100&thumbnailHeight=100&thumbnailFormat=PNG&cachebuster={Math.random}

createComment POST
text: comment
assetId: assetId
https://ecsr.io/comments/post

addOrRemoveFromCollections POST
assetId
addToProfile
https://ecsr.io/asset/toggle-profile

deleteFromInventory POST
assetId: assetId
https://ecsr.io/apisite/inventory/v1/delete-from-inventory

getIsFavorited GET
https://ecsr.io/apisite/catalog/v1/favorites/users/{userId}/assets/{assetId}/favorite

createFavorite POST
https://ecsr.io/apisite/catalog/v1/favorites/users/{userId}/assets/{assetId}/favorite

deleteFavorite DELETE
https://ecsr.io/apisite/catalog/v1/favorites/users/{userId}/assets/{assetId}/favorite

### Chat
getChatSettings GET
https://ecsr.io/apisite/chat/v2/chat-settings

getUserConversations GET
https://ecsr.io/apisite/chat/v2/get-user-conversations?pageNumber={pageNumber}&pageSize={pageSize}

markAsRead POST
conversationId
endMessageId
https://ecsr.io/apisite/chat/v2/mark-as-read

startOneToOneConversation POST
participantUserId: userId
https://ecsr.io/apisite/chat/v2/start-one-to-one-conversation

updateTypingStatus POST
isTyping: isTyping
conversationId
https://ecsr.io/apisite/chat/v2/update-user-typing-status

sendMessage POST
conversationId
message
https://ecsr.io/apisite/chat/v2/send-message

multiGetLatestMessages GET
https://ecsr.io/apisite/chat/v2/multi-get-latest-messages?conversationIds={ids}

getMessages GET
https://ecsr.io/apisite/chat/v2/get-messages?conversationId={conversationId}&pageSize={pageSize}&exclusiveStartMessageId={exclusiveStartMessageId}

### Develop
uploadAsset POST
name: name
assetType: assetTypeId
file: file
optional: groupId: groupId
https://ecsr.io/develop/upload

uploadAssetVersion POST
assetId: assetId
file: file
https://ecsr.io/develop/upload-version

getCreatedAssetDetails POST
assetIds
https://ecsr.io/apisite/itemconfiguration/v1/creations/get-asset-details

getCreatedItems GET
https://ecsr.io/apisite/itemconfiguration/v1/creations/get-assets?assetType={assetType}&limit={limit}&cursor={cursor}
optional: &groupId={groupId}

updateAsset PATCH
name
description
genres
isCopyingAllowed
enableComments
https://ecsr.io/apisite/develop/v1/assets/{assetId}

setAssetPrice POST
priceInRobux or priceInTickets
https://ecsr.io/apisite/itemconfiguration/v1/assets/{assetId}/update-price

getAllGenres GET
https://ecsr.io/apisite/develop/v1/assets/genres

setUniverseMaxPlayers PATCH
maxPlayers
https://ecsr.io/apisite/develop/v1/universes/{universeId}/max-player-count

### Economy
getResellers GET
https://ecsr.io/apisite/economy/v1/assets/assetId/resellers?limit={limit}&cursor={cursor}

getRobux GET
https://ecsr.io/apisite/economy/v1/users/{userId}/currency

getRobuxGroup
https://ecsr.io/apisite/economy/v1/groups/{groupId}/currency

getResellableCopies GET
https://ecsr.io/apisite/economy/v1/assets/{assetId}/users/{userId}/resellable-copies

purchaseItem POST
assetId
expectedPrice: price
expectedSellerId: sellerId
userAssetId
expectedCurrency
https://ecsr.io/apisite/economy/v1/purchases/products/{productId}

setResellableAssetPrice PATCH
price
https://ecsr.io/apisite/economy/v1/assets/{assetId}/resellable-copies/{userAssetId}

getResaleData GET
https://ecsr.io/apisite/economy/v1/assets/{assetId}/resale-data

getTransactions GET
https://ecsr.io/apisite/economy/v2/users/{userId}/transactions?cursor={cursor}&transactionType={type}

getGroupTransactions GET
https://ecsr.io/apisite/economy/v2/groups/{groupId}/transactions?cursor={cursor}&transactionType={type}

getTransactionSummary GET
https://ecsr.io/apisite/economy/v2/users/{userId}/transaction-totals?timeFrame={timePeriod}&transactionType=summary

getGroupTransactionSummary GET
https://ecsr.io/apisite/economy/v2/groups/{groupId}/transaction-totals?timeFrame={timePeriod}&transactionType=summary

getMarketActivity GET
https://ecsr.io/apisite/economy/v2/currency-exchange/market/activity

createCurrencyExchangeOrder POST
amount
sourceCurrency: currency
isMarketOrder
desiredRate
https://ecsr.io/apisite/economy/v2/currency-exchange/orders/create

countOpenPositions GET
Note: Get open position count for authenticated user
https://ecsr.io/apisite/economy/v2/currency-exchange/orders/my/count?currency={currency}

getOpenPositions GET
https://ecsr.io/apisite/economy/v2/currency-exchange/orders/my?limit={limit}&startId={startId}&currency={currency}

closePosition POST
https://ecsr.io/apisite/economy/v2/currency-exchange/orders/{orderId}/close

### Forums
getPostsInSubcategory GET
https://ecsr.io/apisite/forums/v1/sub-category/{subCategoryId}/posts?limit={limit}&cursor={cursor}

getRepliesToThread 
https://ecsr.io/apisite/forums/v1/threads/{threadId}/replies?limit={limit}&cursor={cursor}

getThreadInfoById GET
https://ecsr.io/apisite/forums/v1/threads/{threadId}/info

getPostById GET
https://ecsr.io/apisite/forums/v1/posts/{postId}/info

markAsRead POST
https://ecsr.io/apisite/forums/v1/posts/{postId}/mark-as-read

createThread POST
post
subject
https://ecsr.io/apisite/forums/v1/sub-category/{subCategoryId}/thread

replyToPost POST
post
https://ecsr.io/apisite/forums/v1/posts/{postId}/reply

getSubCategoryInfo GET
https://ecsr.io/apisite/forums/v1/sub-category/{subCategoryId}/info

deletePost DELETE
https://ecsr.io/apisite/forums/v1/posts/{postId}

getPostsByUser GET
https://ecsr.io/apisite/forums/v1/users/{userId}/posts?limit={limit}&cursor={offset}

### Friends
getFriends GET
https://ecsr.io/apisite/friends/v1/user/friend-requests/count

getFollowersCount GET
https://ecsr.io/apisite/friends/v1/users/{userId}/followers/count

getFollowers GET
https://ecsr.io/apisite/friends/v1/users/{userId}/followers?cursor={cursor}&sort={sort}&limit={limit}

getFollowingsCount GET
https://ecsr.io/apisite/friends/v1/users/{userId}/followings/count

getFollowings GET
https://ecsr.io/apisite/friends/v1/users/{userId}/followings?cursor={cursor}&sort={sort}&limit={limit}

getFriendStatus GET
https://ecsr.io/apisite/friends/v1/users/{authenticatedUserId}/friends/statuses?userIds={userId}

getFriendRequests GET
https://ecsr.io/apisite/friends/v1/my/friends/requests?limit={limit}&cursor={cursor}

unfriendUser POST
https://ecsr.io/apisite/friends/v1/users/{userId}/unfriend

acceptFriendRequest POST
https://ecsr.io/apisite/friends/v1/users/{userId}/accept-friend-request

declineFriendRequest POST
https://ecsr.io/apisite/friends/v1/users/{userId}/decline-friend-request

sendFriendRequest POST
https://ecsr.io/apisite/friends/v1/users/{userId}/request-friendship

followUser POST
https://ecsr.io/apisite/friends/v1/users/{userId}/follow

unfollowUser POST
https://ecsr.io/apisite/friends/v1/users/{userId}/unfollow

getFollowingStatus POST
targetUserIds: userIds
https://ecsr.io/apisite/friends/v1/user/following-exists

### Games
getUserGames GET
https://ecsr.io/apisite/games/v2/users/{userId}/games?cursor={cursor}

getGroupGames GET
https://ecsr.io/apisite/games/v2/groups/{groupId}/games?cursor={cursor}

getGameSorts GET
https://ecsr.io/apisite/games/v1/games/sorts?gameSortsContext={gameSortsContext}

getGameList GET
https://ecsr.io/apisite/games/v1/games/list?sortToken={sortToken}&maxRows={limit}&genre={genre}&keyword={keyword}

getGameMedia GET
https://ecsr.io/apisite/games/v2/games/{universeId}/media

launchGame GET
https://ecsr.io/game/get-join-script?placeId={placeId}

multiGetPlaceDetails GET
https://ecsr.io/apisite/games/v1/games/multiget-place-details?placeIds={placeIds}

multiGetUniverseDetails GET
https://ecsr.io/apisite/games/v1/games?universeIds={universeIds}

getServers GET
https://ecsr.io/games/getgameinstancesjson?placeId={placeId}&startIndex={offset}

multiGetGameVotes GET
https://ecsr.io/apisite/games/v1/games/votes?universeIds={universeIds}

voteOnGame PATCH
vote: isUpvote
https://ecsr.io/apisite/games/v1/games/{universeId}/user-votes

### Groups
getUserGroups GET
https://ecsr.io/apisite/groups/v1/users/{userId}/groups/roles

getPermissionsForRoleset GET
https://ecsr.io/apisite/groups/v1/groups/{groupId}/roles/{rolesetId}/permissions

joinGroup POST
https://ecsr.io/apisite/groups/v1/groups/{groupId}/users

leaveGroup DELETE
https://ecsr.io/apisite/groups/v1/groups/{groupId}/users/{userId}

setStatus PATCH
https://ecsr.io/apisite/groups/v1/groups/{groupId}/status

createGroup POST
name: name
description: description
icon: file
https://ecsr.io/apisite/groups/v1/groups/create

getRoles GET
https://ecsr.io/apisite/groups/v1/groups/{groupId}/roles

getMembers GET
https://ecsr.io/apisite/groups/v1/groups/{groupId}/users?cursor={cursor}&limit=${limit}&sortOrder=${sortOrder}

getRolesetMembers GET
https://ecsr.io/apisite/groups/v1/groups/{groupId}/roles/{roleSetId}/users?cursor={cursor}&limit={limit}&sortOrder={sortOrder}

getWall GET
https://ecsr.io/apisite/groups/v2/groups/{groupId}/wall/posts?sortOrder={sort}&limit={limit}&cursor={cursor}

postToWall POST
body: content
https://ecsr.io/apisite/groups/v1/groups/{groupId}/wall/posts

deletePost DELETE
https://ecsr.io/apisite/groups/v1/groups/{groupId}/wall/posts/{postId}

getInfo GET
https://ecsr.io/apisite/groups/v1/groups/{groupId}

claimGroupOwnership POST
https://ecsr.io/apisite/groups/v1/groups/{groupId}/claim-ownership

setGroupAsPrimary POST
groupId
https://ecsr.io/apisite/groups/v1/groups/v1/user/groups/primary

removePrimaryGroup DELETE
https://ecsr.io/apisite/groups/v1/user/groups/primary

getPrimaryGroup GET
https://ecsr.io/apisite/groups/v1/users/{userId}/groups/primary/role

setUserRole PATCH
roleId: roleId
https://ecsr.io/apisite/groups/v1/groups/{groupId}/users/{userId}

setGroupIcon PATCH
file: icon
https://ecsr.io/apisite/groups/v1/groups/icon?groupId={groupId}

setGroupDescription PATCH
description
https://ecsr.io/apisite/groups/v1/groups/{groupId}/description

getGroupSettings GET
https://ecsr.io/apisite/groups/v1/groups/{groupId}/settings

setGroupSettings PATCH
isApprovalRequired
areEnemiesAllowed
areGroupFundsVisible
areGroupGamesVisible
https://ecsr.io/apisite/groups/v1/groups/{groupId}/settings

changeGroupOwner PATCH
userId
https://ecsr.io/apisite/groups/v1/groups/{groupId}/change-owner

createRole POST
name
description
rank
https://ecsr.io/apisite/groups/v1/groups/{groupId}/rolesets/create

editRole PATCH
name
description
rank
https://ecsr.io/apisite/groups/v1/groups/{groupId}/rolesets

deleteRole DELETE
https://ecsr.io/apisite/groups/v1/groups/{groupId}/rolesets

setRolePermissions PATCH
permissions: permissions
https://ecsr.io/apisite/groups/v1/groups/{groupId}/roles/{roleId}/permissions

oneTimePayout POST
PayoutType: 'FixedAmount
Recipients: [{recipientId: userId, recipientType: 'User', amount, }]
https://ecsr.io/apisite/groups/v1/groups/{groupId}/payouts

getGroupInfo GET
https://ecsr.io/apisite/groups/v1/groups/{groupId}

getGroupAuditLog GET
https://ecsr.io/apisite/groups/v1/groups/{groupId}/audit-log?cursor={cursor}&action={action}&userId={userId}&sortOrder=desc&limit=100

### Inventory
getOwnedCopies GET
https://ecsr.io/apisite/inventory/v1/users/{userId}/items/Asset/{assetId}

getInventory GET
https://ecsr.io/inventory/list-json?userId={userId}&assetTypeId={assetTypeId}&cursor={cursor}&itemsPerPage={limit}

getFavorites GET
https://ecsr.io/users/favorites/list-json?userId={userId}&assetTypeId={assetTypeId}&pageNumber={cursor}&itemsPerPage={limit}

getCollections GET
https://ecsr.io/users/profile/robloxcollections-json?userId={userId}

getCollectibleInventory GET
https://ecsr.io/apisite/inventory/v1/users/{userId}/assets/collectibles?cursor={cursor}&limit={limit}&assetType={assetTypeId}

getCollectibleOwners GET
https://ecsr.io/apisite/inventory/v2/assets/{assetId}/owners?cursor={cursor}&limit={limit}&sortOrder={sort}

### Presence
multiGetPresence POST
userIds
https://ecsr.io/apisite/presence/v1/presence/users

### Private Messages
sendMessage POST
recipientid: userId
body
subject
replyMessageId
includePreviousMessage
https://ecsr.io/apisite/privatemessages/v1/messages/send

getAnnouncements GET
https://ecsr.io/apisite/privatemessages/v1/announcements

getMessages GET
https://ecsr.io/apisite/privatemessages/v1/messages?messageTab={tab}&pageSize={limit}&pageNumber={offset/limit}

toggleReadStatus POST
messageIds
https://ecsr.io/apisite/privatemessages/v1/messages/{isRead: mark-read/mark-unread}

toggleArchiveStatus POST
messageIds
https://ecsr.io/apisite/privatemessages/v1/messages/{isArchived: archive/unarchive}

getUnreadMessageCount GET
https://ecsr.io/apisite/privatemessages/v1/messages/unread/count

### Thumbnails
multiGetUserThumbnails GET
https://ecsr.io/apisite/thumbnails/v1/users/avatar?userIds={userIds}&size={size}&format={format}

multiGetUserHeadshots GET
https://ecsr.io/apisite/thumbnails/v1/users/avatar-headshot?userIds={pending}&size={size}&format={format}

multiGetOutfitThumbnails GET
https://ecsr.io/apisite/thumbnails/v1/users/outfits?userOutfitIds={userOutfitIds}&size={size}&format={format}

multiGetGroupIcons GET
https://ecsr.io/apisite/thumbnails/v1/groups/icons?groupIds={groupIds}&format=png&size=420x420

multiGetAssetThumbnails GET
https://ecsr.io/apisite/thumbnails/v1/assets?assetIds={assetIds}&format=png&size=420x420

multiGetUniverseIcons GET
https://ecsr.io/apisite/thumbnails/v1/games/icons?size={size}&format=png&universeIds={item}

### Trades

getMyTrades GET
https://ecsr.io/apisite/trades/v1/trades/{tradeType}?cursor={cursor}

getTradeDetails GET
https://ecsr.io/apisite/trades/v1/trades/{tradeId}

acceptTrade POST
https://ecsr.io/apisite/trades/v1/trades/{tradeId}/accept

declineTrade POST
https://ecsr.io/apisite/trades/v1/trades/{tradeId}/decline

getInboundTradeCount GET
https://ecsr.io/apisite/trades/v1/trades/inbound/count

createTrade POST
offers: [{robux: offerRobux, userAssetIds: offerUserAssets, userId: offerUserId,}, {robux: requestRobux, userAssetIds: requestUserAssets, userId: requestUserId,}]
https://ecsr.io/apisite/trades/v1/trades/send

counterTrade POST
offers: [{robux: offerRobux, userAssetIds: offerUserAssets, userId: offerUserId,}, {robux: requestRobux, userAssetIds: requestUserAssets, userId: requestUserId,}]
https://ecsr.io/apisite/trades/v1/trades/counter

### Users
getMyInfo GET
https://ecsr.io/apisite/users/v1/users/authenticated

getUserInfo GET
https://ecsr.io/apisite/users/v1/users/{userId}

getUserStatus GET
https://ecsr.io/apisite/users/v1/users/{userId}/status

updateStatus PATCH
status: newStatus
https://ecsr.io/apisite/users/v1/users/{userId}/status

getPreviousUsernames GET
https://ecsr.io/apisite/users/v1/users/{userId}/username-history?limit=100&cursor={cursor}

searchUsers GET
https://ecsr.io/apisite/users/results?keyword={keyword}&maxRows={limit}&startIndex={offset}

getMembershipType GET
https://ecsr.io/apisite/premiumfeatures/v1/users/{userId}/validate-membership

getUserIdByUsername POST
usernames: username
https://ecsr.io/apisite/users/v1/usernames/users
