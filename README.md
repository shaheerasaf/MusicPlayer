# Semester Project 
## CS-101
## Said Nabi


# Group Members
1. Shaheer Asaf | 2024574
2. Shanzeh Siddiqui | 2024580
3. Fatima Khalil | 2024176


#Music Player using C++

# Main Features
1. PLay/Pasue Songs
2. Forward/Rewind Songs
3. Skipping Songs

## Types of Users
1. User

## Requirements
1. Function
2. Array
3. Control Structure

#include <iostream>
#include <string>
using namespace std;

// Function declarations
void displayMenu();
void playMusic(string songList[], int currentIndex, bool& isPlaying);
void pauseMusic(string songList[], int currentIndex, bool& isPlaying);
void skipSong(string songList[], int& currentIndex, int totalSongs, bool& isPlaying);
void forwardMusic(string songList[], int currentIndex);
void rewindMusic(string songList[], int currentIndex);

int main() {
    // Array of song names
    string songList[] = {"Song A", "Song B", "Song C", "Song D", "Song E"};
    int totalSongs = sizeof(songList) / sizeof(songList[0]);  // Calculate the number of songs

    bool isPlaying = false;
    int currentIndex = 0;  // to track the current song
    int choice;

    while (true) {
        displayMenu();
        cin >> choice;

        switch (choice) {
            case 1: // Play
                playMusic(songList, currentIndex, isPlaying);
                break;

            case 2: // Pause
                pauseMusic(songList, currentIndex, isPlaying);
                break;

            case 3: // Skip (Move to next song)
                skipSong(songList, currentIndex, totalSongs, isPlaying);
                break;

            case 4: // Forward
                forwardMusic(songList, currentIndex);
                break;

            case 5: // Rewind
                rewindMusic(songList, currentIndex);
                break;

            case 6: // Exit
                cout << "Exiting music player." << endl;
                return 0;

            default:
                cout << "Invalid choice" << endl;
        }
    }

    return 0;
}

// Function to display the menu
void displayMenu() {
    cout << "Music Player" << endl;
    cout << "1. Play" << endl;
    cout << "2. Pause" << endl;
    cout << "3. Skip" << endl;
    cout << "4. Forward" << endl;
    cout << "5. Rewind" << endl;
    cout << "6. Exit" << endl;
    cout << "Enter your choice: ";
}

// Function to play music
void playMusic(string songList[], int currentIndex, bool& isPlaying) {
    if (!isPlaying) {
        isPlaying = true;
        cout << "Playing: " << songList[currentIndex] << endl;  // Access song with arrays
    } else {
        cout << songList[currentIndex] << " is already playing." << endl;
    }
}

// Function to pause music
void pauseMusic(string songList[], int currentIndex, bool& isPlaying) {
    if (isPlaying) {
        isPlaying = false;
        cout << "Paused: " << songList[currentIndex] << endl;  // Access song with arrays
    } else {
        cout << "Music is already paused." << endl;
    }
}

// Function to skip to the next song
void skipSong(string songList[], int& currentIndex, int totalSongs, bool& isPlaying) {
    currentIndex = (currentIndex + 1) % totalSongs;  // Go to the next song or loop
    cout << "Skipped to: " << songList[currentIndex] << endl;  // Access song with arrays
    isPlaying = true;
}

// Function to fast forward the current song
void forwardMusic(string songList[], int currentIndex) {
    cout << "Fast forwarding " << songList[currentIndex] << "..." << endl;  // Access song using array indexing
}

// Function to rewind the current song
void rewindMusic(string songList[], int currentIndex) {
    cout << "Rewinding " << songList[currentIndex] << "..." << endl;  // Access song using array indexing

}


