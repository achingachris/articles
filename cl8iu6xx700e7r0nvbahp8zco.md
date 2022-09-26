## How to fetch and Add Data in React from an API

In my first week in phase 2 of Moringa School Software Engineering classes, I covered the basics of getting data from APIs and working with forms. The Code Challenge for the week had the following tasks:

1. Fetch Transactions from an API and tabulate them.
2. Add new transactions. The transaction added should be posted to the backend API.
3. FIlter out transactions by description

The initial code for the challenge is in this [commit](https://github.com/achingachris/phase2-week1-codechallenge/tree/ee4bdba8aec6821633fd7944e868e1f6a03b072a).

%[https://github.com/achingachris/phase2-week1-codechallenge/tree/ee4bdba8aec6821633fd7944e868e1f6a03b072a]

Before I started, I installed [concurrently](https://www.npmjs.com/package/concurrently) an npm package that allows one to run multiple commands concurrently. Like npm run watch-js & npm run watch-less but better. I wanted to run both react server and json.db server from one script:

`npm run dev`

```json
  "scripts": {
    "start": "PORT=8000 react-scripts start",
    "server": "json-server --watch db.json -p 8001",
    "dev": "concurrently \"npm start\" \"npm run server\""
  },
```

## Fetch Transactions from an API and tabulate them.

I edited the `Transaction.js` file:

```js
import React from "react";

function Transaction() {
  return (
    <tr>
      <td>{"your code here..."}</td>
      <td>{"your code here..."}</td>
      <td>{"your code here..."}</td>
      <td>{"your code here..."}</td>
    </tr>
  );
}

export default Transaction;
```

First, the `transaction` prop will be added, passing in data rendered from the API.
From the API, data will have the following: id, date, description, category, and amount. So I updated the component to:

```js
import React from 'react'

function Transaction({ transaction }) {
  return (
    <tr>
      <td>{transaction.date}</td>
      <td>{transaction.description}</td>
      <td>{transaction.category}</td>
      <td>{transaction.amount}</td>
    </tr>
  )
}

export default Transaction
```

Next step, I climbed up to the `TransactionList` component, where I was supposed to render the data.

```js
import React from "react";
import Transaction from "./Transaction";

function TransactionsList() {
  return (
    <table className="ui celled striped padded table">
      <tbody>
        <tr>
          <th>
            <h3 className="ui center aligned header">Date</h3>
          </th>
          <th>
            <h3 className="ui center aligned header">Description</h3>
          </th>
          <th>
            <h3 className="ui center aligned header">Category</h3>
          </th>
          <th>
            <h3 className="ui center aligned header">Amount</h3>
          </th>
        </tr>
        {/* render a list of <Transaction> components here */}
      </tbody>
    </table>
  );
}

export default TransactionsList;
```

I added the prop `transaction` to the component, so I can fetch data from the upper-level component, `AccountContainer`. The data returned will be an array. So I mapped through the array "transaction" and displayed each item in a table.

```js
{transaction.map((data) => (
    <Transaction key={data.id} transaction={data} />
))}
```

Here is the updated component:

```js
import React from 'react'
import Transaction from './Transaction'

function TransactionsList({ transaction }) {
  return (
    <table className='ui celled striped padded table'>
      <tbody>
        <tr>
          <th>
            <h3 className='ui center aligned header'>Date</h3>
          </th>
          <th>
            <h3 className='ui center aligned header'>Description</h3>
          </th>
          <th>
            <h3 className='ui center aligned header'>Category</h3>
          </th>
          <th>
            <h3 className='ui center aligned header'>Amount</h3>
          </th>
        </tr>
        {transaction.map((data) => (
          <Transaction key={data.id} transaction={data} />
        ))}
      </tbody>
    </table>
  )
}

export default TransactionsList
```

Next is to climb up to a higher level component: `AccountContainer`

```js
import React from "react";
import TransactionsList from "./TransactionsList";
import Search from "./Search";
import AddTransactionForm from "./AddTransactionForm";

function AccountContainer() {
  return (
    <div>
      <Search />
      <AddTransactionForm />
      <TransactionsList />
    </div>
  );
}

export default AccountContainer;
```

I used Hooks and useEffects to get data from the API.

```js
import React, { useEffect, useState } from 'react'
import TransactionsList from './TransactionsList'
import Search from './Search'
import AddTransactionForm from './AddTransactionForm'

function AccountContainer() {
  const [searchItem, setSearchItem] = useState('')
  const [transactions, setTransactions] = useState([])

  // get transactions from API
  useEffect(() => {
    fetch('http://localhost:8001/transactions')
      .then((response) => response.json())
      .then((data) => {
        setTransactions(data)
      })
  }, [])

  return (
    <div>
      <Search />
      <AddTransactionForm />
      <TransactionsList transaction={transactions} />
    </div>
  )
}

export default AccountContainer
```

Running the server to view the changes:

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1664198387938/h08cfu0Sq.png align="left")

## Add new transactions. The transaction added should be posted to the backend API.

To add new transaction, I started with the `AddTransactionForm` component.

```js
import React from "react";

function AddTransactionForm() {
  return (
    <div className="ui segment">
      <form className="ui form">
        <div className="inline fields">
          <input type="date" name="date" />
          <input type="text" name="description" placeholder="Description" />
          <input type="text" name="category" placeholder="Category" />
          <input type="number" name="amount" placeholder="Amount" step="0.01" />
        </div>
        <button className="ui button" type="submit">
          Add Transaction
        </button>
      </form>
    </div>
  );
}

export default AddTransactionForm;
```

First I install `uuid` to assign a unique ID to every transaction added.

`npm i uuid`

Then used state hooks to capture values, and create an event handler to send the data to the API once the form is submitted:

```js
  const handleChange = (e) => {
    e.preventDefault()
    const newTransaction = {
      id: uuid(),
      date: date,
      description: description,
      category: category,
      amount: amount,
    }
    fetch('http://localhost:8001/transactions', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
      },
      body: JSON.stringify(newTransaction),
    })
      .then((resp) => resp.json())
      .then((newQuestion) => console.log(newQuestion))
  }
```

The updated component:

```js
import React, { useState } from 'react'
import { v4 as uuid } from 'uuid'

function AddTransactionForm() {
  const [description, setDescription] = useState('')
  const [amount, setAmount] = useState('')
  const [date, setDate] = useState('')
  const [category, setCategory] = useState('')

  const handleDescriptionChange = (event) => {
    setDescription(event.target.value)
  }

  const handleAmountChange = (event) => {
    setAmount(event.target.value)
  }

  const handleDateChange = (event) => {
    setDate(event.target.value)
  }

  const handleCategoryChange = (event) => {
    setCategory(event.target.value)
  }

  const handleChange = (e) => {
    e.preventDefault()
    const newTransaction = {
      id: uuid(),
      date: date,
      description: description,
      category: category,
      amount: amount,
    }
    fetch('http://localhost:8001/transactions', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
      },
      body: JSON.stringify(newTransaction),
    })
      .then((resp) => resp.json())
      .then((newQuestion) => console.log(newQuestion))
  }

  return (
    <div className='ui segment' onSubmit={handleChange}>
      <form className='ui form'>
        <div className='inline fields'>
          <input
            type='date'
            name='date'
            value={date}
            onChange={handleDateChange}
            required
          />
          <input
            type='text'
            name='description'
            placeholder='Description'
            value={description}
            onChange={handleDescriptionChange}
            required
          />
          <input
            type='text'
            name='category'
            placeholder='Category'
            value={category}
            onChange={handleCategoryChange}
            required
          />
          <input
            type='number'
            name='amount'
            placeholder='Amount'
            step='0.01'
            onChange={handleAmountChange}
            required
          />
        </div>
        <button className='ui button' type='submit'>
          Add Transaction
        </button>
      </form>
    </div>
  )
}

export default AddTransactionForm
```

Running the server to view changes:

%[https://youtu.be/Pfk2fylJdr8]

## FIlter out transactions by description

Inside the `Search` component:

```js
import React from "react";

function Search() {
  return (
    <div className="ui large fluid icon input">
      <input
        type="text"
        placeholder="Search your Recent Transactions"
        onChange={() => console.log("Searching...")}
      />
      <i className="circular search link icon"></i>
    </div>
  );
}

export default Search;
```

I added two props: `({ search, onSearchChange }) `

```js


import React from 'react'

function Search({ search, onSearchChange }) {
  return (
    <div className='ui large fluid icon input'>
      <input
        type='text'
        placeholder='Search your Recent Transactions'
        onChange={onSearchChange}
        value={search}
      />
      <i className='circular search link icon'></i>
    </div>
  )
}

export default Search
```

Next, inside the `AccountContainer` component, I wrote the logic to filter out data. I updated the Search component:

```js
  <Search search={searchItem} onSearchChange={searchFilteredItems} />
```

`searchItem` is from the state hooks:

```js
 const [searchItem, setSearchItem] = useState('')
```

`searchFilteredItems` is a function:

```js
  const searchFilteredItems = (e) => {
    setSearchItem(e.target.value)
    // console.log(searchItem)
  }
```
That updates the value to of the input to the latest input as a user keys in.  Created a function to filter trough the response array and return only transactions that match the search input:

```js
  const displaySearchItems = transactions.filter((transaction) =>
    transaction.description.toLowerCase().includes(searchItem.toLowerCase())
  )
```

Updated the `TransactionsList` component to use the filtered items.

```js
<TransactionsList transaction={displaySearchItems} />
```

The updated file: `AccountContainer.js `

```js
import React, { useEffect, useState } from 'react'
import TransactionsList from './TransactionsList'
import Search from './Search'
import AddTransactionForm from './AddTransactionForm'

function AccountContainer() {
  const [searchItem, setSearchItem] = useState('')
  const [transactions, setTransactions] = useState([])

  // get transations from API
  useEffect(() => {
    fetch('http://localhost:8001/transactions')
      .then((response) => response.json())
      .then((data) => {
        setTransactions(data)
      })
  }, [])

  const searchFilteredItems = (e) => {
    setSearchItem(e.target.value)
    // console.log(searchItem)
  }

  // console.log(typeof transactions)

  const displaySearchItems = transactions.filter((transaction) =>
    transaction.description.toLowerCase().includes(searchItem.toLowerCase())
  )

  console.log(displaySearchItems)
  // const displaySearchItems = transactions.filter((item) => {
  //   return item.name.includes(searchItem)
  // })

  return (
    <div>
      <Search search={searchItem} onSearchChange={searchFilteredItems} />
      <AddTransactionForm />
      <TransactionsList transaction={displaySearchItems} />
    </div>
  )
}

export default AccountContainer
```

Running the server:

%[https://youtu.be/v0EtDmb6YMQ]

## Conclusion

Successfully displayed data using useState and passed it dynamically to Tables. Users can add a new transaction and search for transactions based on descriptions.

## Complete Source

%[https://github.com/achingachris/phase2-week1-codechallenge]





