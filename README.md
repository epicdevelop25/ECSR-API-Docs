# ECSR:R Unofficial API Documentation
**Unofficial Swagger UI Documentation for the ECSR.io API**

[Live Demo & Swagger UI](https://ecsr-api-docs.vercel.app/)

> ⚠️ **Usage Notice**  
> • Do **not** use these endpoints for malicious activities.  
> • Ensure any application you build complies with ECSR’s Terms of Service.  
>
> 🔒 **Private Testing (Coming Soon)**  
> You will soon be able to provide a `.ROBLOSECURITY` cookie at the top of the site to fully test authenticated endpoints.

---
## Inventory

#### GET `/inventory/v1/users/{userId}/items/Asset/{assetId}`
- **OperationId**: `getOwnedCopies`

#### GET `/inventory/list-json?userId={userId}&assetTypeId={assetTypeId}`
- **OperationId**: `getInventory`
- **Optional**: `cursor`, `itemsPerPage`

#### GET `/users/favorites/list-json?userId={userId}&assetTypeId={assetTypeId}`
- **OperationId**: `getFavorites`
- **Optional**: `pageNumber`, `itemsPerPage`

#### GET `/users/profile/robloxcollections-json?userId={userId}`
- **OperationId**: `getCollections`

#### GET `/inventory/v1/users/{userId}/assets/collectibles?cursor={cursor}&limit={limit}`
- **OperationId**: `getCollectibleInventory`

#### GET `/inventory/v2/assets/{assetId}/owners?cursor={cursor}&limit={limit}`
- **OperationId**: `getCollectibleOwners`

---
## Account Information

#### GET `/accountinformation/v1/users/{userId}/roblox-badges`
- **OperationId**: `getUserRobloxBadges`
- **Path Parameter**: `userId` (string)

#### POST `/accountinformation/v1/description`
- **OperationId**: `setUserDescription`
- **Body**:
  ```json
  { "description": "<newDescription>" }
  ```

---
## Account Settings

#### GET `/accountsettings/v1/email`
- **OperationId**: `getMyEmail`

#### GET `/accountsettings/v1/inventory-privacy`
- **OperationId**: `getInventoryPrivacy`

#### POST `/accountsettings/v1/inventory-privacy`
- **OperationId**: `setInventoryPrivacy`
- **Body**:
  ```json
  { "inventoryPrivacy": "<newPrivacy>" }
  ```

#### GET `/accountsettings/v1/trade-privacy`
- **OperationId**: `getTradePrivacy`

#### POST `/accountsettings/v1/trade-privacy`
- **OperationId**: `setTradePrivacy`
- **Body**:
  ```json
  { "tradePrivacy": "<newPrivacy>" }
  ```

#### GET `/accountsettings/v1/trade-value`
- **OperationId**: `getTradeValue`

#### POST `/accountsettings/v1/trade-value`
- **OperationId**: `setTradeValue`
- **Body**:
  ```json
  { "tradeValue": <newValue> }
  ```

---
## Ads

#### POST `/ads/v1/user-ads/{Type}/create?assetId={assetId}`
- **OperationId**: `uploadAdvertisement`
- **Path Parameter**: `Type` (string)
- **Query Parameter**: `assetId` (string)
- **Form Data**: `name` (string), `files` (file)

#### GET `/ads/v1/user-ads/{creatorType}/{creatorId}`
- **OperationId**: `getAds`
- **Path Parameters**: `creatorType` (User | Group), `creatorId` (string)

#### POST `/ads/v1/user-ads/{adId}/run`
- **OperationId**: `bidOnAd`
- **Path Parameter**: `adId` (string)
- **Body**:
  ```json
  { "robux": <number> }
  ```

---
## API

#### GET `/api/alerts/alert-info`
- **OperationId**: `getAlert`

---
## Auth

#### POST `/auth/v2/login`
- **OperationId**: `login`
- **Form Data**: 
  - `ctype`: "username"
  - `cvalue`: `<username>`
  - `password`: `<password>`

#### POST `/auth/v2/logout`
- **OperationId**: `logout`

#### POST `/auth/v2/user/passwords/change`
- **OperationId**: `changePassword`
- **Form Data**:
  - `currentPassword`: `<existingPassword>`
  - `newPassword`: `<newPassword>`

#### GET `/auth/v1/usernames/validate?username={username}&context={context}`
- **OperationId**: `validateUsername`

#### POST `/auth/v1/username`
- **OperationId**: `changeUsername`
- **Form Data**:
  - `username`: `<newUsername>`
  - `password`: `<password>`

#### POST `/auth/v2/logoutfromallsessionsandreauthenticate`
- **OperationId**: `logoutFromAllOtherSessions`

---
## Avatar

#### GET `/avatar/v1/avatar-rules`
- **OperationId**: `getRules`

#### GET `/avatar/v1/users/{userId}/avatar`
- **OperationId**: `getAvatar`
- **Path Parameter**: `userId` (string)

#### GET `/avatar/v1/avatar`
- **OperationId**: `getMyAvatar`

#### POST `/avatar/v1/avatar/redraw-thumbnail`
- **OperationId**: `redrawMyAvatar`

#### POST `/avatar/v1/avatar/v1/avatar/set-wearing-assets`
- **OperationId**: `setWearingAssets`
- **Body**:
  ```json
  { "assetIds": ["<id1>", "<id2>"] }
  ```

#### POST `/avatar/v1/avatar/v1/avatar/set-body-colors`
- **OperationId**: `setColors`
- **Body**:
  ```json
  { "bodyColors": { /* color map */ } }
  ```

#### GET `/avatar/v1/users/{userId}/outfits?itemsPerPage=50&page=1`
- **OperationId**: `getOutfits`

#### POST `/avatar/v1/outfits/create`
- **OperationId**: `createOutfit`
- **Form Data**: `name`: `<outfitName>`

#### POST `/avatar/v1/outfits/{outfitId}/wear`
- **OperationId**: `wearOutfit`

#### POST `/avatar/v1/outfits/{outfitId}/delete`
- **OperationId**: `deleteOutfit`

#### PATCH `/avatar/v1/outfits/{outfitId}`
- **OperationId**: `renameOutfit`
- **Body**:
  ```json
  { "name": "<newName>" }
  ```

---
## Catalog

#### GET `/catalog/v1/search/items?category={category}&limit={limit}&sortType={sortType}`
- **OperationId**: `searchCatalog`
- **Optional Query**: `cursor`, `keyword`, `subcategory`, `creatorTargetId`, `creatorType`

#### GET `/api/marketplace/productinfo?assetId={assetId}`
- **OperationId**: `getProductInfoLegacy`
- **Note**: Hidden server‑side API

#### POST `/catalog/v1/catalog/items/details`
- **OperationId**: `getItemDetails`
- **Body**:
  ```json
  { "itemType": "Asset", "id": "<id>" }
  ```

#### GET `/catalog/v1/recommendations/asset/{assetTypeId}?contextAssetId={assetId}&numItems={limit}`
- **OperationId**: `getRecommendations`

#### GET `/comments/get-json?assetId={assetId}&startIndex={offset}`
- **OperationId**: `getComments`
- **Defaults**: `thumbnailWidth=100`, `thumbnailHeight=100`, `thumbnailFormat=PNG`

#### POST `/comments/post`
- **OperationId**: `createComment`
- **Body**:
  ```json
  { "text": "<comment>", "assetId": "<assetId>" }
  ```

#### POST `/asset/toggle-profile`
- **OperationId**: `addOrRemoveFromCollections`
- **Body**:
  ```json
  { "assetId": "<assetId>", "addToProfile": <true|false> }
  ```

#### POST `/inventory/v1/delete-from-inventory`
- **OperationId**: `deleteFromInventory`
- **Body**:
  ```json
  { "assetId": "<assetId>" }
  ```

#### GET `/catalog/v1/favorites/users/{userId}/assets/{assetId}/favorite`
- **OperationId**: `getIsFavorited`

#### POST `/catalog/v1/favorites/users/{userId}/assets/{assetId}/favorite`
- **OperationId**: `createFavorite`

#### DELETE `/catalog/v1/favorites/users/{userId}/assets/{assetId}/favorite`
- **OperationId**: `deleteFavorite`

---
## Chat

#### GET `/chat/v2/chat-settings`
- **OperationId**: `getChatSettings`

#### GET `/chat/v2/get-user-conversations?pageNumber={pageNumber}&pageSize={pageSize}`
- **OperationId**: `getUserConversations`

#### POST `/chat/v2/mark-as-read`
- **OperationId**: `markAsRead`
- **Body**:
  ```json
  { "conversationId": "<id>", "endMessageId": "<id>" }
  ```

#### POST `/chat/v2/start-one-to-one-conversation`
- **OperationId**: `startOneToOneConversation`
- **Body**:
  ```json
  { "participantUserId": "<userId>" }
  ```

#### POST `/chat/v2/update-user-typing-status`
- **OperationId**: `updateTypingStatus`
- **Body**:
  ```json
  { "isTyping": <boolean>, "conversationId": "<id>" }
  ```

#### POST `/chat/v2/send-message`
- **OperationId**: `sendMessage`
- **Body**:
  ```json
  { "conversationId": "<id>", "message": "<text>" }
  ```

#### GET `/chat/v2/multi-get-latest-messages?conversationIds={ids}`
- **OperationId**: `multiGetLatestMessages`

#### GET `/chat/v2/get-messages?conversationId={conversationId}&pageSize={pageSize}`
- **OperationId**: `getMessages`

---
## Develop

#### POST `/develop/upload`
- **OperationId**: `uploadAsset`
- **Form Data**: 
  - `name` (string)  
  - `assetType` (string)  
  - `groupId` (string, optional)  
  - `file` (file)

#### POST `/develop/upload-version`
- **OperationId**: `uploadAssetVersion`
- **Body**:
  ```json
  { "assetId": "<assetId>" }
  ```
- **Form Data**: `file`

#### POST `/itemconfiguration/v1/creations/get-asset-details`
- **OperationId**: `getCreatedAssetDetails`
- **Body**:
  ```json
  { "assetIds": ["<id1>", "<id2>"] }
  ```

#### GET `/itemconfiguration/v1/creations/get-assets?assetType={assetType}&limit={limit}`
- **OperationId**: `getCreatedItems`
- **Query**: `assetType`, `limit`, `cursor` (optional), `groupId` (optional)

#### PATCH `/develop/v1/assets/{assetId}`
- **OperationId**: `updateAsset`
- **Body**: any of:
  ```json
  {
    "name": "<string>",
    "description": "<string>",
    "genres": ["<genre1>","<genre2>"],
    "isCopyingAllowed": <boolean>,
    "enableComments": <boolean>
  }
  ```

#### POST `/itemconfiguration/v1/assets/{assetId}/update-price`
- **OperationId**: `setAssetPrice`
- **Body**:
  ```json
  { "priceInRobux": <int>, "priceInTickets": <int> }
  ```

#### GET `/develop/v1/assets/genres`
- **OperationId**: `getAllGenres`

#### PATCH `/develop/v1/universes/{universeId}/max-player-count`
- **OperationId**: `setUniverseMaxPlayers`
- **Body**:
  ```json
  { "maxPlayers": <int> }
  ```

---
## Economy

#### GET `/economy/v1/assets/{assetId}/resellers?limit={limit}`
- **OperationId**: `getResellers`

#### GET `/economy/v1/users/{userId}/currency`
- **OperationId**: `getRobux`

#### GET `/economy/v1/groups/{groupId}/currency`
- **OperationId**: `getRobuxGroup`

#### GET `/economy/v1/assets/{assetId}/users/{userId}/resellable-copies`
- **OperationId**: `getResellableCopies`

#### POST `/economy/v1/purchases/products/{productId}`
- **OperationId**: `purchaseItem`
- **Body**:
  ```json
  {
    "assetId":"<string>",
    "expectedPrice":<number>,
    "expectedSellerId":"<string>",
    "userAssetId":"<string>",
    "expectedCurrency":"<string>"
  }
  ```

#### PATCH `/economy/v1/assets/{assetId}/resellable-copies/{userAssetId}`
- **OperationId**: `setResellableAssetPrice`
- **Body**:
  ```json
  { "price": <number> }
  ```

#### GET `/economy/v1/assets/{assetId}/resale-data`
- **OperationId**: `getResaleData`

#### GET `/economy/v2/users/{userId}/transactions` (optional `?cursor=…&transactionType=…`)
- **OperationId**: `getTransactions`

#### GET `/economy/v2/groups/{groupId}/transactions` (optional `?cursor=…&transactionType=…`)
- **OperationId**: `getGroupTransactions`

#### GET `/economy/v2/users/{userId}/transaction-totals?timeFrame={timeFrame}`
- **OperationId**: `getTransactionSummary`

#### GET `/economy/v2/groups/{groupId}/transaction-totals?timeFrame={timeFrame}`
- **OperationId**: `getGroupTransactionSummary`

#### GET `/economy/v2/currency-exchange/market/activity`
- **OperationId**: `getMarketActivity`

#### POST `/economy/v2/currency-exchange/orders/create`
- **OperationId**: `createCurrencyExchangeOrder`
- **Body**:
  ```json
  { "amount":<number>, "sourceCurrency":"<string>", "isMarketOrder":<boolean>, "desiredRate":<number> }
  ```

#### GET `/economy/v2/currency-exchange/orders/my/count?currency={currency}`
- **OperationId**: `countOpenPositions`

#### GET `/economy/v2/currency-exchange/orders/my` (optional `?limit=…&startId=…&currency=…`)
- **OperationId**: `getOpenPositions`

#### POST `/economy/v2/currency-exchange/orders/{orderId}/close`
- **OperationId**: `closePosition`

---
## Forums

#### GET `/forums/v1/sub-category/{subCategoryId}/posts?limit={limit}`
- **OperationId**: `getPostsInSubcategory`

#### GET `/forums/v1/threads/{threadId}/replies?limit={limit}`
- **OperationId**: `getRepliesToThread`

#### GET `/forums/v1/threads/{threadId}/info`
- **OperationId**: `getThreadInfoById`

#### GET `/forums/v1/posts/{postId}/info`
- **OperationId**: `getPostById`

#### POST `/forums/v1/posts/{postId}/mark-as-read`
- **OperationId**: `markAsReadForum`

#### POST `/forums/v1/sub-category/{subCategoryId}/thread`
- **OperationId**: `createThread`
- **Body**:
  ```json
  { "subject":"<string>", "post":"<string>" }
  ```

#### POST `/forums/v1/posts/{postId}/reply`
- **OperationId**: `replyToPost`
- **Body**:
  ```json
  { "post":"<string>" }
  ```

#### GET `/forums/v1/sub-category/{subCategoryId}/info`
- **OperationId**: `getSubCategoryInfo`

#### DELETE `/forums/v1/posts/{postId}`
- **OperationId**: `deletePostForum`

#### GET `/forums/v1/users/{userId}/posts?limit={limit}`
- **OperationId**: `getPostsByUser`

---
## Friends

#### GET `/friends/v1/user/friend-requests/count`
- **OperationId**: `getFriends`

#### GET `/friends/v1/users/{userId}/followers/count`
- **OperationId**: `getFollowersCount`

#### GET `/friends/v1/users/{userId}/followers` (optional `?cursor=…&sort=…&limit=…`)
- **OperationId**: `getFollowers`

#### GET `/friends/v1/users/{userId}/followings/count`
- **OperationId**: `getFollowingsCount`

#### GET `/friends/v1/users/{userId}/followings` (optional `?cursor=…&sort=…&limit=…`)
- **OperationId**: `getFollowings`

#### GET `/friends/v1/users/{authenticatedUserId}/friends/statuses?userIds={userIds}`
- **OperationId**: `getFriendStatus`

#### GET `/friends/v1/my/friends/requests?limit={limit}`
- **OperationId**: `getFriendRequests`

#### POST `/friends/v1/users/{userId}/unfriend`
- **OperationId**: `unfriendUser`

#### POST `/friends/v1/users/{userId}/accept-friend-request`
- **OperationId**: `acceptFriendRequest`

#### POST `/friends/v1/users/{userId}/decline-friend-request`
- **OperationId**: `declineFriendRequest`

#### POST `/friends/v1/users/{userId}/request-friendship`
- **OperationId**: `sendFriendRequest`

#### POST `/friends/v1/users/{userId}/follow`
- **OperationId**: `followUser`

#### POST `/friends/v1/users/{userId}/unfollow`
- **OperationId**: `unfollowUser`

#### POST `/friends/v1/user/following-exists`
- **OperationId**: `getFollowingStatus`
- **Body**:
  ```json
  { "targetUserIds": ["<id1>", "<id2>"] }
  ```

---
## Games

#### GET `/games/v2/users/{userId}/games` (optional `?cursor=…`)
- **OperationId**: `getUserGames`

#### GET `/games/v2/groups/{groupId}/games` (optional `?cursor=…`)
- **OperationId**: `getGroupGames`

#### GET `/games/v1/games/sorts?gameSortsContext={context}`
- **OperationId**: `getGameSorts`

#### GET `/games/v1/games/list?sortToken={sortToken}&maxRows={limit}`
- **OperationId**: `getGameList`
- **Optional**: `genre`, `keyword`

#### GET `/games/v2/games/{universeId}/media`
- **OperationId**: `getGameMedia`

#### GET `/game/get-join-script?placeId={placeId}`
- **OperationId**: `launchGame`

#### GET `/games/v1/games/multiget-place-details?placeIds={placeIds}`
- **OperationId**: `multiGetPlaceDetails`

#### GET `/games/v1/games?universeIds={universeIds}`
- **OperationId**: `multiGetUniverseDetails`

#### GET `/games/getgameinstancesjson?placeId={placeId}` (optional `&startIndex=…`)
- **OperationId**: `getServers`

#### GET `/games/v1/games/votes?universeIds={universeIds}`
- **OperationId**: `multiGetGameVotes`

#### PATCH `/games/v1/games/{universeId}/user-votes`
- **OperationId**: `voteOnGame`
- **Body**:
  ```json
  { "vote": <true|false> }
  ```

---
## Groups

#### GET `/groups/v1/users/{userId}/groups/roles`
- **OperationId**: `getUserGroups`

#### GET `/groups/v1/groups/{groupId}/roles/{rolesetId}/permissions`
- **OperationId**: `getPermissionsForRoleset`

#### POST `/groups/v1/groups/{groupId}/users`
- **OperationId**: `joinGroup`

#### DELETE `/groups/v1/groups/{groupId}/users/{userId}`
- **OperationId**: `leaveGroup`

#### PATCH `/groups/v1/groups/{groupId}/status`
- **OperationId**: `setStatus`

#### POST `/groups/v1/groups/create`
- **OperationId**: `createGroup`
- **Form Data**:
  - `name`, `description`, `icon`

#### GET `/groups/v1/groups/{groupId}/roles`
- **OperationId**: `getRoles`

#### GET `/groups/v1/groups/{groupId}/users` (optional `?cursor=…&limit=…&sortOrder=…`)
- **OperationId**: `getMembers`

#### GET `/groups/v1/groups/{groupId}/roles/{rolesetId}/users` (optional `?cursor=…&limit=…&sortOrder=…`)
- **OperationId**: `getRolesetMembers`

#### GET `/groups/v2/groups/{groupId}/wall/posts` (optional `?sortOrder=…&limit=…&cursor=…`)
- **OperationId**: `getWall`

#### POST `/groups/v1/groups/{groupId}/wall/posts`
- **OperationId**: `postToWall`
- **Body**:
  ```json
  { "content":"<string>" }
  ```

#### DELETE `/groups/v1/groups/{groupId}/wall/posts/{postId}`
- **OperationId**: `deleteWallPost`

#### GET `/groups/v1/groups/{groupId}`
- **OperationId**: `getGroupInfo`

#### POST `/groups/v1/groups/{groupId}/claim-ownership`
- **OperationId**: `claimGroupOwnership`

#### POST `/groups/v1/groups/v1/user/groups/primary?groupId={groupId}`
- **OperationId**: `setGroupAsPrimary`

#### DELETE `/groups/v1/user/groups/primary`
- **OperationId**: `removePrimaryGroup`

#### GET `/groups/v1/users/{userId}/groups/primary/role`
- **OperationId**: `getPrimaryGroup`

#### PATCH `/groups/v1/groups/icon?groupId={groupId}`
- **OperationId**: `setGroupIcon`
- **Form Data**: `icon`

#### PATCH `/groups/v1/groups/{groupId}/description`
- **OperationId**: `setGroupDescription`
- **Body**:
  ```json
  { "description":"<string>" }
  ```

#### GET `/groups/v1/groups/{groupId}/settings`
- **OperationId**: `getGroupSettings`

#### PATCH `/groups/v1/groups/{groupId}/settings`
- **OperationId**: `setGroupSettings`
- **Body**:
  ```json
  { "isApprovalRequired":<boolean>, "areEnemiesAllowed":<boolean>, "areGroupFundsVisible":<boolean>, "areGroupGamesVisible":<boolean> }
  ```

#### PATCH `/groups/v1/groups/{groupId}/change-owner`
- **OperationId**: `changeGroupOwner`
- **Body**:
  ```json
  { "userId":"<string>" }
  ```

#### POST `/groups/v1/groups/{groupId}/rolesets/create`
- **OperationId**: `createRole`
- **Body**:
  ```json
  { "name":"<string>", "description":"<string>", "rank":<int> }
  ```

#### PATCH `/groups/v1/groups/{groupId}/rolesets`
- **OperationId**: `editRole`
- **Body**:
  ```json
  { "name":"<string>", "description":"<string>", "rank":<int> }
  ```

#### DELETE `/groups/v1/groups/{groupId}/rolesets`
- **OperationId**: `deleteRole`

#### PATCH `/groups/v1/groups/{groupId}/roles/{roleId}/permissions`
- **OperationId**: `setRolePermissions`
- **Body**:
  ```json
  { "permissions":["<perm1>","<perm2>"] }
  ```

#### POST `/groups/v1/groups/{groupId}/payouts`
- **OperationId**: `oneTimePayout`
- **Body**:
  ```json
  { "PayoutType":"<string>", "Recipients":[{ "recipientId":"<id>", "recipientType":"<type>", "amount":<number> }] }
  ```

#### GET `/groups/v1/groups/{groupId}/audit-log` (optional `?cursor=…&action=…&userId=…&sortOrder=desc&limit=100`)
- **OperationId**: `getGroupAuditLog`

---
## Inventory

#### GET `/inventory/v1/users/{userId}/items/Asset/{assetId}`
- **OperationId**: `getOwnedCopies`

#### GET `/inventory/list-json?userId={userId}&assetTypeId={assetTypeId}`
- **OperationId**: `getInventory`
- **Optional**: `cursor`, `itemsPerPage`

#### GET `/users/favorites/list-json?userId={userId}&assetTypeId={assetTypeId}`
- **OperationId**: `getFavorites`
- **Optional**: `pageNumber`, `itemsPerPage`

#### GET `/users/profile/robloxcollections-json?userId={userId}`
- **OperationId**: `getCollections`

#### GET `/inventory/v1/users/{userId}/assets/collectibles?cursor={cursor}&limit={limit}`
- **OperationId**: `getCollectibleInventory`

#### GET `/inventory/v2/assets/{assetId}/owners?cursor={cursor}&limit={limit}`
- **OperationId**: `getCollectibleOwners`

---
## Presence

#### POST `/presence/v1/presence/users`
- **OperationId**: `multiGetPresence`
- **Body**:
  ```json
  { "userIds":["<id1>","<id2>"] }
  ```

---
## Private Messages

#### POST `/privatemessages/v1/messages/send`
- **OperationId**: `sendPrivateMessage`
- **Body**:
  ```json
  { "recipientid":"<userId>", "body":"<text>", "subject":"<string>", "replyMessageId":"<id>", "includePreviousMessage":<boolean> }
  ```

#### GET `/privatemessages/v1/announcements`
- **OperationId**: `getAnnouncements`

#### GET `/privatemessages/v1/messages?messageTab={tab}&pageSize={limit}&pageNumber={page}`
- **OperationId**: `getPMMessages`

#### POST `/privatemessages/v1/messages/{isRead}`
- **OperationId**: `toggleReadStatus`
- **Path**: `mark-read` or `mark-unread`
- **Body**:
  ```json
  { "messageIds":["<id1>","<id2>"] }
  ```

#### POST `/privatemessages/v1/messages/{isArchived}`
- **OperationId**: `toggleArchiveStatus`
- **Path**: `archive` or `unarchive`
- **Body**:
  ```json
  { "messageIds":["<id1>","<id2>"] }
  ```

#### GET `/privatemessages/v1/messages/unread/count`
- **OperationId**: `getUnreadMessageCount`

---

#### POST `/privatemessages/v1/messages/send`
- **OperationId**: `sendPrivateMessage`
- **Body**:
  ```json
  { "recipientid":"<userId>", "body":"<text>", "subject":"<string>", "replyMessageId":"<id>", "includePreviousMessage":<boolean> }
  ```

#### GET `/privatemessages/v1/announcements`
- **OperationId**: `getAnnouncements`

#### GET `/privatemessages/v1/messages?messageTab={tab}&pageSize={limit}&pageNumber={page}`
- **OperationId**: `getPMMessages`

#### POST `/privatemessages/v1/messages/{isRead}`
- **OperationId**: `toggleReadStatus`
- **Path**: `mark-read` or `mark-unread`
- **Body**:
  ```json
  { "messageIds":["<id1>","<id2>"] }
  ```

#### POST `/privatemessages/v1/messages/{isArchived}`
- **OperationId**: `toggleArchiveStatus`
- **Path**: `archive` or `unarchive`
- **Body**:
  ```json
  { "messageIds":["<id1>","<id2>"] }
  ```

#### GET `/privatemessages/v1/messages/unread/count`
- **OperationId**: `getUnreadMessageCount`

---
## Thumbnails

#### GET `/thumbnails/v1/users/avatar?userIds={userIds}&size={size}&format={format}`
- **OperationId**: `multiGetUserThumbnails`

#### GET `/thumbnails/v1/users/avatar-headshot?userIds={userIds}&size={size}&format={format}`
- **OperationId**: `multiGetUserHeadshots`

#### GET `/thumbnails/v1/users/outfits?userOutfitIds={userOutfitIds}&size={size}&format={format}`
- **OperationId**: `multiGetOutfitThumbnails`

#### GET `/thumbnails/v1/groups/icons?groupIds={groupIds}&size={size}&format={format}`
- **OperationId**: `multiGetGroupIcons`

#### GET `/thumbnails/v1/assets?assetIds={assetIds}&size={size}&format={format}`
- **OperationId**: `multiGetAssetThumbnails`

#### GET `/thumbnails/v1/games/icons?universeIds={universeIds}&size={size}&format={format}`
- **OperationId**: `multiGetUniverseIcons`

---

#### GET `/trades/v1/trades/{tradeType}?cursor={cursor}`
- **OperationId**: `getMyTrades`

#### GET `/trades/v1/trades/{tradeId}`
- **OperationId**: `getTradeDetails`

#### POST `/trades/v1/trades/{tradeId}/accept`
- **OperationId**: `acceptTrade`

#### POST `/trades/v1/trades/{tradeId}/decline`
- **OperationId**: `declineTrade`

#### GET `/trades/v1/trades/inbound/count`
- **OperationId**: `getInboundTradeCount`

#### POST `/trades/v1/trades/send`
- **OperationId**: `createTrade`
- **Body**:
  ```json
  { "offers":[{ "robux":<number>,"userAssetIds":["<id>"],"userId":"<id>" }], "requests":[...] }
  ```

#### POST `/trades/v1/trades/counter`
- **OperationId**: `counterTrade`
- **Body**: same structure as createTrade

---
## Users

#### GET `/users/v1/users/authenticated`
- **OperationId**: `getMyInfo`

#### GET `/users/v1/users/{userId}`
- **OperationId**: `getUserInfo`

#### GET `/users/v1/users/{userId}/status`
- **OperationId**: `getUserStatus`

#### PATCH `/users/v1/users/{userId}/status`
- **OperationId**: `updateStatus`
- **Body**:
  ```json
  { "status":"<string>" }
  ```

#### GET `/users/v1/users/{userId}/username-history?limit={limit}`
- **OperationId**: `getPreviousUsernames`

#### GET `/users/results?keyword={keyword}&maxRows={limit}&startIndex={offset}`
- **OperationId**: `searchUsers`

#### GET `/premiumfeatures/v1/users/{userId}/validate-membership`
- **OperationId**: `getMembershipType`

#### POST `/users/v1/usernames/users`
- **OperationId**: `getUserIdByUsername`
- **Body**:
  ```json
  { "usernames":["<username1>",...]}  
  ```
