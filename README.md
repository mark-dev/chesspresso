My fork of chesspresso jtsay362-edition

I try use chesspresso for [parsing lichess database](https://github.com/mark-dev/chessfactory-hall-of-fame) and had to fix some critical bugs for handle pgn games from lichess.

 
 1. Fix pgn parse bug - appears when two knight can move to same square, but one of them are pinned. 
    
    According rules, correct pgn in this case, are not contain knight column, like Nbc2, due only one knight can move.
    
    Original code can choose wrong knight, that cause incorrect position.
    
    (seems developer forgot about knights when implementing scenario when pinned piece can move across pin direction)
    
    eg: https://lichess.org/S2VYc7Fg#72
 2. Adhock for supporting enhanced png syntax like.
    ``` 1. e4 { [%eval 0.17] [%clk 0:00:30] } 1... c5 { [%eval 0.19] [%clk 0:00:30] } ```
    
    Old code recognize % like escape symbol. 
    
    But according pgn syntax ,escape mechanizm are triggeres by % "appearing in the firstcolumn of a line"
    
    http://rpm.pbone.net/index.php3/stat/45/idpl/19488088/numer/3/nazwa/Games::Chess::PGN
    
    Now '%' ignored, if previous symbol was '['
    
 3. Also some [Position](src/main/java/chesspresso/position/Position.java) methods are exposed
    
