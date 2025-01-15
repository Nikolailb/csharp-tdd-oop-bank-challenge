# Domain Model
| Classes               | Methods/Properties                              | Scenarios                                                                                                         | Outputs                                       |
| --------------------- | ----------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- | --------------------------------------------- |
| AccountTransaction.cs | Guid Account                                    | The ID of the account owning the transaction                                                                      |                                               |
| AccountTransaction.cs | Amount                                          | The amount of founds involved in the transaction, negative when withdrawing.                                      |                                               |
| AccountTransaction.cs | Created                                         | The creation time for the transaction.                                                                            |                                               |
| Account.cs            | Transactions                                    | List of the performed transactions in the account.                                                                |                                               |
| Account.cs            | Branch                                          | Which branch the account belongs to.                                                                              | Enum                                          |
| Account.cs            | AccountId                                       | Unique Id of the account                                                                                          | Guid                                          |
| Account.cs            | Name                                            | The name of the account                                                                                           | String                                        |
| Account.cs            | WriteStatement(IStatementWriter)                | Writes the account statement using the provided writer.                                                           |                                               |
| Account.cs            | Balance                                         | Calculates the current balance based on the list of transactions.                                                 |                                               |
| Account.cs            | Deposit(double)                                 | Deposits an amount into the account                                                                               |                                               |
| Account.cs            | Withdraw(double)                                | Withdraws an amount from the account, if available                                                                |                                               |
| SavingsAccount.cs     | WithdrawalLimit                                 | The upper limit of a single withdrawal from a SavingsAccount                                                      |                                               |
| SavingsAccount.cs     | WithdrawalLock                                  | A dated lock on withdrawal from the account. Withdrawals will be opened after the datetime of the lock has passed |                                               |
| Bank.cs               | OverdraftRequests                               | A list of the yet to be processed overdraft requests.                                                             |                                               |
| Bank.cs               | CreateAccount(string, Branch)                   | Creates a regular account at the bank.                                                                            |                                               |
| Bank.cs               | CreateAccount(string, double, DateTime, Branch) | Creates a Savings account in the bank                                                                             |                                               |
| Bank.cs               | GetAccount(Guid)                                | Gets and account by its ID                                                                                        | Account                                       |
| Bank.cs               | RequestOverdraft(Guid, double)                  | Adds a overdraft request to the bank                                                                              |                                               |
| Bank.cs               | HandleOverdraft(int, bool)                      | Handles acceptance / rejection of overdraft requests                                                              |                                               |
| Bank.cs               | GetOverdraftRequest(Guid)                       | Gets all the overdraft requests tied to the account                                                               |                                               |
| Bank.cs               | GetOverdraftRequest(int)                        | Gets a specific overdraft request by ID                                                                           |                                               |
| Bank.cs               | GetOverdraftStatus(int)                         | Gets the status of an overdraft request                                                                           | 0 for rejected, 1 for pending, 2 for accepted |