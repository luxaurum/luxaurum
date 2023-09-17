<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lux Aurum Blockchain</title>
    <script src="https://brython.info/brython.js"></script>
</head>
<body>
    <h1>Lux Aurum Blockchain Example</h1>
    <div id="blockchain"></div>
    <button onclick="addBlock()">Add Block</button>

    <script type="text/python">
        import hashlib
        import time

        class Block:
            def __init__(self, index, previous_hash, data, timestamp, vote=None, allocation=None):
                self.index = index
                self.previous_hash = previous_hash
                self.data = data
                self.timestamp = timestamp
                self.vote = vote
                self.allocation = allocation
                self.hash = self.calculate_hash()

            def calculate_hash(self):
                value = str(self.index) + self.previous_hash + str(self.timestamp) + self.data + str(self.vote) + str(self.allocation)
                return hashlib.sha256(value.encode()).hexdigest()

        class VotingBlockchain:
            def __init__(self):
                self.chain = [self.create_genesis_block()]

            def create_genesis_block(self):
                return Block(0, "0", "Genesis Block", int(time.time()))

            def get_latest_block(self):
                return self.chain[-1]

            def add_block(self, new_block):
                new_block.previous_hash = self.get_latest_block().hash
                new_block.hash = new_block.calculate_hash()
                self.chain.append(new_block)

        class AllocationBlockchain:
            def __init__(self):
                self.chain = [self.create_genesis_block()]

            def create_genesis_block(self):
                return Block(0, "0", "Genesis Block", int(time.time()))

            def get_latest_block(self):
                return self.chain[-1]

            def add_block(self, new_block):
                new_block.previous_hash = self.get_latest_block().hash
                new_block.hash = new_block.calculate_hash()
                self.chain.append(new_block)

        # Creating separate blockchain instances for voting and allocation
        voting_blockchain = VotingBlockchain()
        allocation_blockchain = AllocationBlockchain()

        # Simulating a voting process
        voters = ["Alice", "Bob", "Charlie"]
        votes = {"Alice": "Candidate A", "Bob": "Candidate B", "Charlie": "Candidate A"}

        for voter in voters:
            vote_data = f"Voted for {votes[voter]}"  # Simulated vote data
            timestamp = int(time.time())
            new_block = Block(len(voting_blockchain.chain), voting_blockchain.get_latest_block().hash, vote_data, timestamp, votes[voter])
            voting_blockchain.add_block(new_block)

        # Simulating fund allocation
        allocations = {"Education": 3000, "Public Workers": 5000, "Department of Justice": 2000}

        for purpose, amount in allocations.items():
            allocation_data = f"Allocated {amount} to {purpose}"  # Simulated allocation data
            timestamp = int(time.time())
            new_block = Block(len(allocation_blockchain.chain), allocation_blockchain.get_latest_block().hash, allocation_data, timestamp, allocation=amount)
            allocation_blockchain.add_block(new_block)

        # Display the voting blockchain
        voting_blockchain_html = "<h2>Voting Blockchain:</h2><ul>"
        for block in voting_blockchain.chain:
            voting_blockchain_html += f"<li>Block {block.index} - Timestamp: {block.timestamp}</li>"
            voting_blockchain_html += f"<li>Data: {block.data}</li>"
            voting_blockchain_html += f"<li>Vote: {block.vote}</li>"
            voting_blockchain_html += f"<li>Previous Hash: {block.previous_hash}</li>"
            voting_blockchain_html += f"<li>Hash: {block.hash}</li><br>"
        voting_blockchain_html += "</ul>"

        # Display the allocation blockchain
        allocation_blockchain_html = "<h2>Allocation Blockchain:</h2><ul>"
        for block in allocation_blockchain.chain:
            allocation_blockchain_html += f"<li>Block {block.index} - Timestamp: {block.timestamp}</li>"
            allocation_blockchain_html += f"<li>Data: {block.data}</li>"
            allocation_blockchain_html += f"<li>Allocation: {block.allocation}</li>"
            allocation_blockchain_html += f"<li>Previous Hash: {block.previous_hash}</li>"
            allocation_blockchain_html += f"<li>Hash: {block.hash}</li><br>"
        allocation_blockchain_html += "</ul>"

        # Display both blockchains
        document.getElementById('blockchain').innerHTML = voting_blockchain_html + allocation_blockchain_html

        </script>
    </body>
</html>
