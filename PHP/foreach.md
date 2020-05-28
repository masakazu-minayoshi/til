```
<?php
//foreach:複数の値を出力
$members = [
  'name' => '本田',
  'height' => '189',
  'hobby' => 'cooking'
];
//valueのみ表示
foreach($members as $member) {
  echo $member;
}
echo '<br>';
//keyとvalue表示
foreach($members as $key => $value) {
  echo $key . 'は' . $value . 'です';
}
// 多段階の配列を展開したい時
$members_2 = [
  '本田' => [
    'height' => '189',
    'hobby' => 'cooking'
  ],
  '佐藤' => [
    'height' => '170',
    'hobby' => 'cooking'
  ]
];
echo '<br>';
foreach($members_2 as $member_1) {
  foreach($member_1 as $member){
    echo $member . 'は' . $value . 'です';
  }
}
?>
```
