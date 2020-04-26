# ffmpeg-tools

[(English)](README-en.md)

## インストール

1. まず[このツールのzipファイル](https://github.com/hkawash/ffmpeg-tools/archive/master.zip)をダウンロードし、zipを展開します。
2. ffmpeg を[こちらのサイト](https://ffmpeg.zeranoe.com/builds/)からダウンロードして展開します。
   - Version はリリース版（4.2.2など）でよいです。Architecture でOSを選びます。
   - Linking は Static のままとしておきます。
   - ダウンロードサイトは[ffmpeg の元サイト](https://www.ffmpeg.org/download.html)からたどってもよいです。
3. 展開してできたフォルダをたどり、bin というフォルダの下にある ffmpeg.exe (Macはffmpeg) を、1で展開した `ffmpeg-tools-master` フォルダの中に入れておきます。

すでに ffmpeg をインストール済みの場合、2, 3のステップは不要です。環境変数でパスを設定していないならば .bat や .sh 内の `PATH` を編集してパスを通しておきます。面倒な場合は 3のステップのようにファイルをコピーしておきます。


## 音声付きパワーポイントの圧縮

音声付きパワーポイントのファイル (pptxやppsx)を圧縮します。「挿入 > オーディオ > オーディオの録音」で作成された音声付きパワーポイントを想定しています。

- 内部に含まれる m4a の音声ファイルのビットレートを64kbpsに圧縮します。
- 画像は「書式/図の形式 > 図の圧縮」などで別途圧縮しておいてください。
- 動画も「ファイル > 情報 > メディアの圧縮」などで圧縮しておいてください。


### 使い方

1. 音声付きpptxもしくはppsxファイルを `ffmpeg-tools-master` フォルダの `ppt-in` という名前のフォルダに入れておきます。
   - 複数のファイルを入れてもOKです。
2. スクリプトを実行します（<a href="#note1">実行時の注意点</a>も参考にしてください）。
   - Windows: `compress_pptaudio-win.bat` をダブルクリックします。
   - Mac (Linux, Windowsのbash): ターミナルを開いて `compress_pptaudio-mac.sh` を実行します。
3. `ppt-out` という名前のフォルダに、圧縮された pptx や ppsx ファイルが出力されます。

<a name="note1"></a>

### 実行時の注意点

#### Windows

- **ダウンロードしてから初めて実行するときは、「WindowsによってPCが保護されました」と表示されるので、「詳細情報」をクリックしてから「実行」を選んでください。**
- 黒い画面が開きますが、勝手に閉じるまで待ってください。
- 同時に何回も実行しないでください。

#### Mac (および Linux や Windowsのbash)

1. bash の使えるターミナルを開きます。Macは Launchpad や Spotlightで、ter.. ぐらいを打ち込むとターミナルを選べます。）
1. ffmpeg-tools フォルダへ移動します。Macで、[書類] の下に `ffmpeg-tools` というフォルダで展開したのであれば、以下を打ち込んでフォルダを移動します。
    ```
    cd /Users/<ユーザ名>/Documents/ffmpeg-tools-master
    ```
    （上のコマンドを打ち込んだあと、最後に return を押します。途中でtabキーを押すとファイル名などが補完できます。`<ユーザ名>`のところには、PCで使っている自分のユーザ名を入れます。）
1. ターミナルで以下を打ち込んで return キーを押し、スクリプトを実行します。
    ```
    ./compress_pptaudio-mac.sh
    ```

### その他

- このスクリプトでは、内部の m4a ファイルを 64kbps にします。これ以外のビットレートにするには、スクリプト内の `BITRATE` を変更してください。
- m4a 以外のオーディオファイルが挿入されていて、これを圧縮対象とするには、スクリプト内の `m4a` のあたりを変更してください。
