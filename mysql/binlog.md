# binlogについて
 - レコードの更新内容を保存する
 - 誤ってデータを削除した場合の復元などにも使用できる
 - マスタースレーブ構成で2つ以上のデータベースサーバーが存在する場合、マスタサーバからスレーブサーバにbinlogの内容を転送する
   - スレーブサーバがbinlogを適用して、マスタサーバのデータと一致性を保つ