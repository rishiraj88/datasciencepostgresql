# Aggregation with Window Partitioning
Postgres offers the following functions for the purpose:
- RANK()
- CAST()
- MAX()

## aggregation query
SELECT
	game_level,
	player_name,
	score,
	RANK() OVER (PARTITION BY game_level ORDER BY score DESC) AS level_rank,
	CAST(AVG(score) OVER (PARTITION BY game_level) AS int) AS level_avg_score,
	MAX(score) OVER (PARTITION BY game_level) AS level_max_score,
	score - MAX(score) OVER (PARTITION BY game_level) AS points_below_max
FROM
	game_scores
ORDER BY
	game_level, level_rank;

## database setup
CREATE TABLE game_scores (
	score_id INT PRIMARY KEY,
	game_level VARCHAR(50),
	player_name VARCHAR(50),
	score INT
);

INSERT INTO game_scores (score_id, game_level, player_name, score) VALUES
-- Level 1: Dragon’s Den
(1, 'Level 1: Dragon’s Den', 'Fatima Ali', 5200),
(2, 'Level 1: Dragon’s Den', 'Carlos Rodriguez', 6000),
(3, 'Level 1: Dragon’s Den', 'Wei Zhang', 5500),
(4, 'Level 1: Dragon’s Den', 'David Smith', 5000),
(5, 'Level 1: Dragon’s Den', 'Aisha Khan', 5800),

-- Level 2: Mystic Forest
(6, 'Level 2: Mystic Forest', 'Fatima Ali', 5400),
(7, 'Level 2: Mystic Forest', 'Carlos Rodriguez', 6300),
(8, 'Level 2: Mystic Forest', 'Wei Zhang', 6100),
(9, 'Level 2: Mystic Forest', 'David Smith', 6200),
(10, 'Level 2: Mystic Forest', 'Aisha Khan', 5800),

-- Level 3: Ancient Ruins
(11, 'Level 3: Ancient Ruins', 'Fatima Ali', 5000),
(12, 'Level 3: Ancient Ruins', 'Carlos Rodriguez', 5100),
(13, 'Level 3: Ancient Ruins', 'Wei Zhang', 5300),
(14, 'Level 3: Ancient Ruins', 'David Smith', 5200),
(15, 'Level 3: Ancient Ruins', 'Aisha Khan', 4900),

-- Level 4: Forgotten Temple
(16, 'Level 4: Forgotten Temple', 'Fatima Ali', 7200),
(17, 'Level 4: Forgotten Temple', 'Carlos Rodriguez', 7000),
(18, 'Level 4: Forgotten Temple', 'Wei Zhang', 7400),
(19, 'Level 4: Forgotten Temple', 'David Smith', 7100),
(20, 'Level 4: Forgotten Temple', 'Aisha Khan', 7300),

-- Level 5: Sky Castle
(21, 'Level 5: Sky Castle', 'Fatima Ali', 6900),
(22, 'Level 5: Sky Castle', 'Carlos Rodriguez', 7100),
(23, 'Level 5: Sky Castle', 'Wei Zhang', 7000),
(24, 'Level 5: Sky Castle', 'David Smith', 6800),
(25, 'Level 5: Sky Castle', 'Aisha Khan', 6600);

SELECT
	score_id,
	game_level,
	player_name,
	score
FROM
	game_scores;

## Mark your feedback at the Following Contact Points
- **LinkedIn:** <https://www.linkedin.com/in/rishirajopenminds>
- **GitHub:** <https://github.com/rishiraj88>

## Credits and Gratitude
- Thank all who have mentored, taught and guided. Also, always appreciate who have supported with pair programming and more.