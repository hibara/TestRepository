# TestRepository

Repository for test embed images on Github.

GitHub上で、README.md 上から、レポジトリ内にあるイメージ画像などのファイルを参照して埋め込む方法をいろいろ実験してみました。

## Relative or Absolute Path

まず、相対パスや、絶対パスでのリンクです。

「N.G.」となっているものは、うまくリンクが貼られずに、画像がうまく表示されていません。

ref. <https://github.community/t/how-do-you-put-images-on-the-readme-md-file/576/5>

`![Test Image 1](image/test.png)` -> O.K.  
![Test Image 1](image/test.png)

パスは合っていても、ダブルコーテーションで括ってしまうとN.G.となります。

`![Test Image 2]("image/test.png")` -> N.G.  
![Test Image 2]("image/test.png")

`![Test Image 3](/image/test.png)` -> O.K.  
![Test Image 3](/image/test.png)

絶対パスでの、レポジトリ内の直接リンクはダメなようです。その際には、次の通りGit上のファイル先を示す「blob」ディレクトリを指定する必要があるようです。

`![Test Image 4](https://github.com/hibara/TestRepository/image/test.png)` -> N.G.  
![Test Image 4](https://github.com/hibara/TestRepository/image/test.png)

とはいえ、以下のように相対パスで「blob」を書いても正しくリンクされないようです。

`![Test Image 5](blob/master/image/test.png)` -> N.G.  
![Test Image 5](blob/master/image/test.png)

絶対パスなら、O.K.

`![Test Image 6](https://github.com/hibara/TestRepository/blob/master/image/test.png)` -> O.K.  
![Test Image 6](https://github.com/hibara/TestRepository/blob/master/image/test.png)

## Raw data

いわゆるGitHub上で画像ファイルを選択すると、そのファイル情報ページへのリンクとなってしまいますが、生データ（raw）なら行けます。

とはいえ、以下のレポジトリのリソースを格納するリンクで表示されるはずなんですが、この場合は、N.G.となっています。これ、どうしてリンクが効かないのか、分かる方は教えていただけると幸いです。

`![Test Image 7](https://raw.githubusercontent.com/hibara/TestRepository/blob/master/image/test.png)` -> N.G.  
![Test Image 7](https://raw.githubusercontent.com/hibara/TestRepository/blob/master/image/test.png)

ref. <https://stackoverflow.com/questions/14494747/add-images-to-readme-md-on-github>

リンクの引数として「raw=true」を渡してやれば、きちんと表示されます。これは相対パスでも行けます。

`![Test Image 8](https://github.com/hibara/TestRepository/blob/master/image/test.png?raw=true)` -> O.K.  
![Test Image 8](https://github.com/hibara/TestRepository/blob/master/image/test.png?raw=true)

`![Test Image 9](image/test.png?raw=true "Test Image Title")` -> O.K.  
![Test Image 9](image/test.png?raw=true "Test Image Title")

## Branch data

レポジトリ上に、README.md 用の画像ディレクトリーがあるのはなんかダサいっていう場合は、ブランチを切ってそこに画像ディレクトリーを作って格納する方法があります。以下のサイトが参考になります。

ref. <https://cakecatz.hatenadiary.com/entry/2015/02/10/214942>

以下の例は、「branch-image」というブランチに、「b-image」という画像ディレクトリを作って画像を格納しています。

試しに、このレポジトリページから、ブランチを「branch-image」に変更してみてください。前述のディレクトリーが表示されると思います。

ちなみに、今まで表示されている画像と区別するために、今回はあえてちがう画像を貼り付けてみました。

`![Test Image 10](https://github.com/hibara/TestRepository/blob/branch-image/b-image/branch-test.png?raw=true)` -> O.K.  
![Test Image 10](https://github.com/hibara/TestRepository/blob/branch-image/b-image/branch-test.png?raw=true)

こうすることで、メインの「master」ブランチにしておけば、その README.md 画像ディレクトリーは表示されずに、画像を裏で参照して表示することが可能です。

とはいえ、私的には、README.md に貼られている画像がどこから来ているのか分からなくなるのは、気持ちが悪いのでこの方法はしないと思います（個人的な感想です）。
