### Project Description
Transactional File Manager is a .NET API that supports including file system operations such as file copy, move, delete, append, etc. in a transaction. It's an implementation of System.Transaction.IEnlistmentNotification (works with System.Transactions.TransactionScope).

This library allows you to wrap file system operations in transactions like this:

```csharp
// Wrap a file copy and a database insert in the same transaction
TxFileManager fileMgr = new TxFileManager();
using (TransactionScope scope1 = new TransactionScope())
{
    // Copy a file
    fileMgr.Copy(srcFileName, destFileName);

    // Insert a database record
    dbMgr.ExecuteNonQuery(insertSql);

    scope1.Complete();
}
```

## Current features
- Support the following file operations in transactions:
    - AppendAllText
    - Copy
    - CreateDirectory
    - DeleteDirectory
    - DeleteFile
    - Move
    - Snapshot
    - WriteAllText

This started out as a [blog post](http://www.chinhdo.com/20080825/transactional-file-manager/) on Chinh's blog. This library supports any file system and is not a wrapper over Transactional NTFS (see [AlphaFS](http://alphafs.codeplex.com/)).

Feedback is very welcome. Also if you have any suggestions for enhancements or bug reports please use the discussions area. Better yet, join this project and contribute yourself. That's how open source works!

## Quick Start
See the [Documentation](https://transactionalfilemgr.codeplex.com/documentation?referringTitle=Home) section for a quick tutorial.

This library is also available from NuGet <https://www.nuget.org/packages/TxFileManager>
Last edited Sep 24, 2014 at 3:13 AM by [chinhdo](https://www.codeplex.com/site/users/view/chinhdo), version 21
