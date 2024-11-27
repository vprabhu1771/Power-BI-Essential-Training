= Table.ReplaceValue(#"Changed Type","a","z",Replacer.ReplaceText,{"Column1"})

= Table.RemoveColumns(#"Replaced Value",{"Column1"})

= Table.RenameColumns(#"Changed Type",{{"PRRICE", "PRICE"}})