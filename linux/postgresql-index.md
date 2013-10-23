### postgresql 索引的建立

1.建立联合索引

    create unique index keyword_created_on on article_matched_keywords (keyword,created_on);

