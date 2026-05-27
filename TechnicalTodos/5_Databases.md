# Databases
- Mostly of 2 types
    - Relational
    - Non-relational

# Relational
- Formatted, structured data
- Rows and columns
- Data organized into 'tables'
- ACID transactions
    - A (*Atomicity*): Each transaction is a single unit, either fails completely or succeeds completely
    - C (*Consistency*): All transactions must bring DB from a consistent state to another, i.e. preserves DB invariants
    - I (*Isolation*): Ensures that concurrent execution of transactions leaves the DB in the same state as if transactions were sequential
    - D (*Durability*): If transaction is committed, in case of of system failure it remains comitted
- Allows for stored procedures, usually the go to in order to keep DB secure

# Non - relational
- Doesn't use structured data, so no tables
- Uses flexible data models such as key-value pairs, documents, graphs, and wide-column stores
- Offers flexibility in data models
- Better at high-speed transactions, rapid access to large volumes of data
- More cost efficient if using commodity hardware and open source software
- Best for:
    - Real time data processing
    - Rapidly and massivly growing datasets
    - Env. where data models change frequently
