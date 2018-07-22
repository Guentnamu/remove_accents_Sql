DROP FUNCTION IF EXISTS `remove_accents`;

DELIMITER //
CREATE FUNCTION `remove_accents`(`str` TEXT)
    RETURNS text
    LANGUAGE SQL
    DETERMINISTIC
    NO SQL
    SQL SECURITY INVOKER
    COMMENT ''

BEGIN

    SET str = LOWER(str);
    SET str = REGEXP_REPLACE(str,'à|á|ạ|ả|ã|â|ầ|ấ|ậ|ẩ|ẫ|ă|ằ|ắ|ặ|ẳ|ẵ','a');
    SET str = REGEXP_REPLACE(str,'è|é|ẹ|ẻ|ẽ|ê|ề|ế|ệ|ể|ễ','e');
    SET str = REGEXP_REPLACE(str,'ì|í|ị|ỉ|ĩ','i');
    SET str = REGEXP_REPLACE(str,'ò|ó|ọ|ỏ|õ|ô|ồ|ố|ộ|ổ|ỗ|ơ|ờ|ớ|ợ|ở|ỡ','o');
    SET str = REGEXP_REPLACE(str,'ù|ú|ụ|ủ|ũ|ư|ừ|ứ|ự|ử|ữ','u');
    SET str = REGEXP_REPLACE(str,'ỳ|ý|ỵ|ỷ|ỹ','y');
    SET str = REGEXP_REPLACE(str,'đ','d');

    RETURN str;
END
//
DELIMITER ;
