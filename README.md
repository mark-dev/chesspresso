My fork of chesspresso jtsay362-edition

I try use it for parsing lichess database

And had to fix some critical bugs for handle pgn games from lichess.

 
 1. Fix pgn parse bug - appears when two knight can move to same square, but one of them are pinned. 
    
    According rules, correct pgn in this case, are not contain knight column, like Nbd5, due only one knight can move.
    
    Old code can choose wrong knight, that cause incorrect position.
    
    eg: https://lichess.org/S2VYc7Fg#72
 2. Adhock for supporting enhanced png syntax like.
    ``` 1. e4 { [%eval 0.17] [%clk 0:00:30] } 1... c5 { [%eval 0.19] [%clk 0:00:30] } ```
    
    Old code recognize % like escape symbol. 
    
    But according pgn syntax ,escape mechanizm are triggeres by % "appearing in the firstcolumn of a line"
    
    http://rpm.pbone.net/index.php3/stat/45/idpl/19488088/numer/3/nazwa/Games::Chess::PGN
    