# Blockchain in Go

This repository contains a simple blockchain implementation in Go. The implementation includes functionalities to insert, list, and verify blocks in the blockchain as well as modify transactions within the blocks.

## Files

- `assignment01IBC.go`: Contains the implementation of the blockchain and its functionalities.
- `main.go`: A sample main file to run and test the blockchain implementation.
- `go.mod`: Go module file.

## Blockchain Functions Implemented

- `CalculateHash`: Calculates the hash of a block based on its transactions.
- `InsertBlock`: Inserts a new block into the blockchain.
- `ChangeBlock`: Changes a transaction in the blockchain and updates the hashes.
- `ListBlocks`: Lists all the blocks in the blockchain.
- `VerifyChain`: Verifies the integrity of the blockchain.

## How to Run

1. Install Go (if not already installed). You can download it from [here](https://golang.org/dl/).
2. Clone this repository to your local machine.
    ```sh
    git clone https://github.com/AmmarAhmedl200961/blockchain-go.git
    ```
3. Navigate to the project directory.
    ```sh
    cd blockchain-go
    ```
4. Run the code.
    ```sh
    go run .
    ```

## Example Usage

The `main.go` file contains an example of how to use the blockchain implementation. It demonstrates creating a blockchain, inserting blocks, listing the blocks, modifying a transaction, and verifying the blockchain.

```
package main
import "fmt"

func main() {
    var chainHead *Block
    genesis := Block{transactions: []string{"S2E", "S2Z"}}
    chainHead = InsertBlock(genesis.transactions, chainHead)
    fmt.Println("Data on Head = ", chainHead.transactions)
    fmt.Println("Hash of current block =", chainHead.currentHash)

    secondBlock := Block{transactions: []string{"E2Alice", "E2Bob", "S2John"}}
    chainHead = InsertBlock(secondBlock.transactions, chainHead)
    fmt.Println("Head of second block = ", chainHead.transactions)
    fmt.Println("Hash of second block = ", chainHead.currentHash)
    fmt.Println("Transactions of previous block (block 1) = ", chainHead.prevPointer.transactions)
    fmt.Println("Hash of previous block (block 1) = ", chainHead.prevPointer.currentHash)

    fmt.Print("\n\nLIST OF BLOCKS\n")
    ListBlocks(chainHead)
    ChangeBlock("S2E", "S2Trudy", chainHead)
    VerifyChain(chainHead)
}
```

## License

This project is licensed under the MIT License.
