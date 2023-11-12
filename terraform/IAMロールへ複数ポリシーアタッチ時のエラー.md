# IAMロールへ複数のポリシーを同時にアタッチしようとした際に発生したエラー
 - `Error: attaching policy arn:aws:iam::aws:policy/AmazonSSMReadOnlyAccess to IAM Role ***-role: ConcurrentModification: Another request updating the entity is in progress. Please try again later.`
   - `status code: 409, request id: *****`

# 原因
 - ポリシーのアタッチには時間がかかり、前のポリシーアタッチ処理が終わるまで次の処理を受け付けてくれない？（推測）

# 回避策
 - ポリシーの作成に任意の待ち時間を与えることで回避できる模様（[参考](https://qiita.com/tak080/items/cc7af67872c21ac8a2d7#%E5%AF%BE%E5%BF%9C)）
 - 単純に複数回applyしても問題なく作成はされる。一発で作成したいときには上記が参考になりそう