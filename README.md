# MuseTrino

MuseScore Studio 4 の再生に、NEUTRINO の歌声を同期させる**非公式**の VST3 プラグインです（Windows 64bit）。
楽譜を書きながら、MuseScore の再生ボタンで、歌詞を付けたパートを NEUTRINO が歌います。

> 本ソフトウェアは STUDIO NEUTRINO の作者、MuseScore の開発元とは無関係の非公式ツールです。
> NEUTRINO 本体と歌声ライブラリは同梱していません。

## ダウンロード

**[最新版のダウンロード（Releases）](https://github.com/wassawasa/MuseTrino/releases/latest)** から `MuseTrino-<版>-win64.zip` を取得してください。

※ このページの緑の「Code」ボタンからダウンロードできるのはこの説明だけで、ソフトウェア本体は入っていません。

## 必要なもの

- Windows 10 / 11（64bit）
- [MuseScore Studio](https://musescore.org/) 4.7 以降（4.7.7 で動作を確認しています）
- [NEUTRINO](https://studio-neutrino.com/) 標準版（Tau v3.2 以降）と歌声ライブラリ

Node.js などのほかのソフトは要りません。

## インストール

1. MuseScore を終了し、zip を展開します
2. 中の `MuseTrino.vst3` フォルダを、中身ごと次のどちらかにコピーします
   - `C:\Program Files\Common Files\VST3`（管理者の許可を求められます）
   - `%LOCALAPPDATA%\Programs\Common\VST3`（自分のユーザーだけで使う場合）
3. MuseScore を起動し、ミキサーで歌のパートの音源を「VST インストゥルメント」→ **MuseTrino** にします
4. MuseTrino を初めて読み込むと、MuseScore 用のプラグイン（`MuseTrino.qml`）が `ドキュメント\MuseScore4\Plugins\MuseTrino` に入ります。MuseScore を一度起動し直し、「プラグイン」→「プラグインを管理」で MuseTrino を有効にします
5. 「プラグイン」メニューから MuseTrino を開き、小さなウィンドウを開いたままにします（パートがいくつあっても 1 つだけ）

NEUTRINO は `C:\NEUTRINO` などから自動で探します。見つからないときは、MuseTrino の画面（ミキサーの音源の歯車）で NEUTRINO 標準版のフォルダを選んでください。

`MuseTrino.vst3` の中には、歌声を作るサービス（`musetrino-service.exe` と `neutrilizer-infer.exe`）も入っています。フォルダの中身は分けずにコピーしてください。

- **更新:** MuseScore を終了して 30 秒ほど待ってから、新しい `MuseTrino.vst3` で上書きします
- **削除:** MuseScore を終了して `MuseTrino.vst3` を消します（MuseScore 用プラグインと `%LOCALAPPDATA%\MuseTrino` も、不要なら消してください）

詳しくは zip に同梱の README.txt を参照してください。

## 主な機能

- MuseScore の再生・再生位置・再生速度に合わせて歌う（MuseScore の「音声を書き出し」にも歌声が入ります）
- 編集は数秒で歌声に反映（変わったフレーズだけ作り直します）
- パートの自動判定、パートごとの声・サポートモデル・スタイル・移調
- 反復の 2 番以降の歌詞、スウィング、強弱記号による音量、ブレス記号での息継ぎ
- 英字のスキャット（woo・doo・bap など）やローマ字の歌詞を仮名にして歌う、「く’ら」の母音の無声化
- 内蔵の高速エンジン: NEUTRINO 標準版の ONNX Runtime と歌声ライブラリを読み込んだまま使い、フレーズごとの待ち時間なしで歌声を作る（計算は標準版と同じ。Neutrilizer と同じもの）
- 歌詞のないパートは、すべての音符を「ら」で歌う
- [Neutrilizer](https://github.com/wassawasa/Neutrilizer) のプロジェクト（.ntlz）への書き出し（パートごと）

## 利用上の注意

- 本ソフトウェアは無保証です。使用によって生じたいかなる損害についても、作者は責任を負いません
- NEUTRINO と各歌声ライブラリは、それぞれの利用規約に従って使用してください。生成した音声の利用も同様です
- 第三者のソフトウェアのライセンス表記は、`MuseTrino.vst3` の中の `Contents\Resources\THIRD-PARTY-NOTICES.txt` にあります
- VST is a registered trademark of Steinberg Media Technologies GmbH.
