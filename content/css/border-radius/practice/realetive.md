🛠 Если вы не уверены, что блок всегда будет квадратным, то для подстраховки можно указывать закругление в абсолютных единицах.  Причём указать значение, бо́льшая чем максимальная ширина и высота блока. Например, `border-radius: 9999px`. Если в этой ситуации указывать закругление в процентах, то значение будет считаться от ширины и высоты. Что приведёт к вытягиванию блока в _яйцо_:

<iframe title="50% скругления" src="../demos/half-radius/" height="590"></iframe>
