# Model  
## 概要  
Model名（単数形）とDB名（複数形）は紐づくようにLaravelでは設定されている.  
（例) Itemモデル⇆itemsテーブル  
※造語や複数形が存在しない単語の時<br>protected…と書いて紐付けるkとができるが極力しない方がよい。  
```
[Entry.php]
<?php

namespace App;

use Illuminate\Database\Eloquent\Model;

class Entry extends Model
{
    //
    protected $table = 'entry-table'
}
```
