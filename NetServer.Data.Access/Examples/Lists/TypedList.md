<properties date="2016-05-11"
/>

```
    using SuperOffice;
    using SuperOffice.CRM.Lists;
                
        SoSession _session = SoSession.Authenticate( "SAL1", "" );
        ISoListProvider mdoProvider = SoLists.GetCurrencyList();
        PrintMdoProvider( "Currency", mdoProvider );
        
        mdoProvider = SoLists.GetCategoryList();
        PrintMdoProvider( "Category", mdoProvider );
        _session.Close();
        
        private void PrintMdoProvider( string listname,
ISoListProvider mdoProvider )
        {
                Console.WriteLine( "\r\n" + listname );
                foreach( ISoListItem item in
mdoProvider.HistoryItems )
                {
                        Console.WriteLine( "[H] {0}|{1}   ({2})",
item.Id, item.Name, item.IconHint );
                }
                Console.WriteLine( "---------------" );
                foreach( ISoListItem item in mdoProvider.RootItems
)
                {
                        Console.WriteLine( "[R] {0}|{1}   ({2})",
item.Id, item.Name, item.IconHint );
                }
                Console.WriteLine( "---------------" );
                foreach( ISoListHeading heading in
mdoProvider.HeadingItems )
                {
                        Console.WriteLine( "[H] {0}|{1}   ({2})",
heading.Heading.Id, heading.Heading.Name, heading.Heading.IconHint
);
                        foreach( ISoListItem item in heading.Items
)
                        {
                                Console.WriteLine( "\t[I] {0}|{1}",
item.Id, item.Name );
                        }
                }
        }
```

See Also:

SoLists
