# Wordle Clone

### Created by
* Aaron Lieberman
* Armanul Ambia
* Iftekharul Islam
* Jacob Nguyen

## Installation

1. Clone the directory
```bash
git clone https://github.com/AaronLieb/WordleClone.git
```

2. Enter the repository directory
```bash
cd WordleClone
```

3. Install the required libraries and tools
```bash
sudo apt update
sudo apt install --yes python3-pip ruby-foreman sqlite3 httpie jq
python3 -m pip install 'fastapi[all]' sqlite-utils
```

4. Go into the `api` directory
```bash
cd api
```

5. Run the initialization script
```bash
./bin/init.sh
```
This will download the wordle wordlists, parse them, create the database, and fill the database

6. Start all the microservices and the load balancer
```bash
./start.sh
```

7. To view the documentation of the endpoints, open the swagger docs

On the port for the microservice use the `/docs/` endpoint to check the available endpoints for that microservice

8. In a separate terminal, you can test the microservices using the scripts in the `bin/endpoint-tests/` directory
Most of the scripts use command line arguments to send words, here is an example of one being used

## Project 2 Endpoints

Check if a guess is a valid five-letter word:
```bash
./bin/endpoint-tests/put_validate.sh <word>
```

Check a guess against the word of the day:
```bash
./bin/endpoint-tests/put_check.sh <word>
```

Add a word to the valid words database:
```bash
./bin/endpoint-tests/post_word.sh <word>
```

Delete a word from the valid words database:
```bash
./bin/endpoint-tests/delete_word.sh <word>
```

Add a word to the answers database:
```bash
./bin/endpoint-tests/post_answer.sh <word>
```

Delete a word from the answers database:
```bash
./bin/endpoint-tests/delete_answer.sh <word>
```

Change the current word of the day to a custom word:
```bash
./bin/endpoint-tests/post_next_answer.sh <word>
```

Remove the custom word of the day and set it back to the original:
```bash
./bin/endpoint-tests/delete_next_answer.sh
```


## Project 3 Endpoints

Test posting win or loss:
```bash
./bin/endpoint-tests/post_win_loss.sh <username> <game_id> <guesses> <won>
```
In this script, 5 argument parameters are passed in, username: int, game_id: int, guesses: int, and won: bool (1 or 0)

Test getting stats:
```bash
./bin/endpoint-tests/get_stats.sh <user_name>
```

Test Getting Users with Most Wins:
```bash
./bin/endpoint-tests/get_top_wins.sh
```

Test Getting Users with Longest Streak:
```bash
./bin/endpoint-tests/get_longest_streak.sh
```


## Project 4 Endpoints

#### NOTE: og_id is the original user integer ID, NOT the user's UUID.

Start a new game for a specific user:
```bash
./bin/p4-endpoints/start_game.sh <og_id> <game_id>
```

Check the guesses made and the number of guess remaining for a specific game a specific user is playing:
```bash
./bin/p4-endpoints/get_game.sh <og_id> <game_id>
```

Make a guess on a specific game for a specific user:
```bash
./bin/p4-endpoints/make_guess.sh <og_id> <game_id> <word>
```
