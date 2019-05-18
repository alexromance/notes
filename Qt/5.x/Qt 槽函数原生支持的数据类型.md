```
// F is a tuple: (QMetaType::TypeName, QMetaType::TypeNameID, RealType)
// ### Qt6: reorder the types to match the C++ integral type ranking
#define QT_FOR_EACH_STATIC_PRIMITIVE_TYPE(F)\
    F(Void, 43, void) \
    F(Bool, 1, bool) \
    F(Int, 2, int) \
    F(UInt, 3, uint) \
    F(LongLong, 4, qlonglong) \
    F(ULongLong, 5, qulonglong) \
    F(Double, 6, double) \
    F(Long, 32, long) \
    F(Short, 33, short) \
    F(Char, 34, char) \
    F(ULong, 35, ulong) \
    F(UShort, 36, ushort) \
    F(UChar, 37, uchar) \
    F(Float, 38, float) \
    F(SChar, 40, signed char) \
    F(Nullptr, 51, std::nullptr_t) \
    F(QCborSimpleType, 52, QCborSimpleType) \

#define QT_FOR_EACH_STATIC_PRIMITIVE_POINTER(F)\
    F(VoidStar, 31, void*) \

#if QT_CONFIG(itemmodel)
#define QT_FOR_EACH_STATIC_ITEMMODEL_CLASS(F)\
    F(QModelIndex, 42, QModelIndex) \
    F(QPersistentModelIndex, 50, QPersistentModelIndex)
#else
#define QT_FOR_EACH_STATIC_ITEMMODEL_CLASS(F)
#endif

#define QT_FOR_EACH_STATIC_CORE_CLASS(F)\
    F(QChar, 7, QChar) \
    F(QString, 10, QString) \
    F(QStringList, 11, QStringList) \
    F(QByteArray, 12, QByteArray) \
    F(QBitArray, 13, QBitArray) \
    F(QDate, 14, QDate) \
    F(QTime, 15, QTime) \
    F(QDateTime, 16, QDateTime) \
    F(QUrl, 17, QUrl) \
    F(QLocale, 18, QLocale) \
    F(QRect, 19, QRect) \
    F(QRectF, 20, QRectF) \
    F(QSize, 21, QSize) \
    F(QSizeF, 22, QSizeF) \
    F(QLine, 23, QLine) \
    F(QLineF, 24, QLineF) \
    F(QPoint, 25, QPoint) \
    F(QPointF, 26, QPointF) \
    F(QRegExp, 27, QRegExp) \
    F(QEasingCurve, 29, QEasingCurve) \
    F(QUuid, 30, QUuid) \
    F(QVariant, 41, QVariant) \
    F(QRegularExpression, 44, QRegularExpression) \
    F(QJsonValue, 45, QJsonValue) \
    F(QJsonObject, 46, QJsonObject) \
    F(QJsonArray, 47, QJsonArray) \
    F(QJsonDocument, 48, QJsonDocument) \
    F(QCborValue, 53, QCborValue) \
    F(QCborArray, 54, QCborArray) \
    F(QCborMap, 55, QCborMap) \
    QT_FOR_EACH_STATIC_ITEMMODEL_CLASS(F)

#define QT_FOR_EACH_STATIC_CORE_POINTER(F)\
    F(QObjectStar, 39, QObject*)

#define QT_FOR_EACH_STATIC_CORE_TEMPLATE(F)\
    F(QVariantMap, 8, QVariantMap) \
    F(QVariantList, 9, QVariantList) \
    F(QVariantHash, 28, QVariantHash) \
    F(QByteArrayList, 49, QByteArrayList) \

#define QT_FOR_EACH_STATIC_GUI_CLASS(F)\
    F(QFont, 64, QFont) \
    F(QPixmap, 65, QPixmap) \
    F(QBrush, 66, QBrush) \
    F(QColor, 67, QColor) \
    F(QPalette, 68, QPalette) \
    F(QIcon, 69, QIcon) \
    F(QImage, 70, QImage) \
    F(QPolygon, 71, QPolygon) \
    F(QRegion, 72, QRegion) \
    F(QBitmap, 73, QBitmap) \
    F(QCursor, 74, QCursor) \
    F(QKeySequence, 75, QKeySequence) \
    F(QPen, 76, QPen) \
    F(QTextLength, 77, QTextLength) \
    F(QTextFormat, 78, QTextFormat) \
    F(QMatrix, 79, QMatrix) \
    F(QTransform, 80, QTransform) \
    F(QMatrix4x4, 81, QMatrix4x4) \
    F(QVector2D, 82, QVector2D) \
    F(QVector3D, 83, QVector3D) \
    F(QVector4D, 84, QVector4D) \
    F(QQuaternion, 85, QQuaternion) \
    F(QPolygonF, 86, QPolygonF) \


#define QT_FOR_EACH_STATIC_WIDGETS_CLASS(F)\
    F(QSizePolicy, 121, QSizePolicy) \

// ### FIXME kill that set
#define QT_FOR_EACH_STATIC_HACKS_TYPE(F)\
    F(QMetaTypeId2<qreal>::MetaType, -1, qreal)

// F is a tuple: (QMetaType::TypeName, QMetaType::TypeNameID, AliasingType, "RealType")
#define QT_FOR_EACH_STATIC_ALIAS_TYPE(F)\
    F(ULong, -1, ulong, "unsigned long") \
    F(UInt, -1, uint, "unsigned int") \
    F(UShort, -1, ushort, "unsigned short") \
    F(UChar, -1, uchar, "unsigned char") \
    F(LongLong, -1, qlonglong, "long long") \
    F(ULongLong, -1, qulonglong, "unsigned long long") \
    F(SChar, -1, signed char, "qint8") \
    F(UChar, -1, uchar, "quint8") \
    F(Short, -1, short, "qint16") \
    F(UShort, -1, ushort, "quint16") \
    F(Int, -1, int, "qint32") \
    F(UInt, -1, uint, "quint32") \
    F(LongLong, -1, qlonglong, "qint64") \
    F(ULongLong, -1, qulonglong, "quint64") \
    F(QVariantList, -1, QVariantList, "QList<QVariant>") \
    F(QVariantMap, -1, QVariantMap, "QMap<QString,QVariant>") \
    F(QVariantHash, -1, QVariantHash, "QHash<QString,QVariant>") \
    F(QByteArrayList, -1, QByteArrayList, "QList<QByteArray>") \

#define QT_FOR_EACH_STATIC_TYPE(F)\
    QT_FOR_EACH_STATIC_PRIMITIVE_TYPE(F)\
    QT_FOR_EACH_STATIC_PRIMITIVE_POINTER(F)\
    QT_FOR_EACH_STATIC_CORE_CLASS(F)\
    QT_FOR_EACH_STATIC_CORE_POINTER(F)\
    QT_FOR_EACH_STATIC_CORE_TEMPLATE(F)\
    QT_FOR_EACH_STATIC_GUI_CLASS(F)\
    QT_FOR_EACH_STATIC_WIDGETS_CLASS(F)\

#define QT_DEFINE_METATYPE_ID(TypeName, Id, Name) \
    TypeName = Id,

#define QT_FOR_EACH_AUTOMATIC_TEMPLATE_1ARG(F) \
    F(QList) \
    F(QVector) \
    F(QQueue) \
    F(QStack) \
    F(QSet) \
    F(QLinkedList)

#define QT_FOR_EACH_AUTOMATIC_TEMPLATE_2ARG(F) \
    F(QHash, class) \
    F(QMap, class) \
    F(QPair, struct)

#define QT_FOR_EACH_AUTOMATIC_TEMPLATE_SMART_POINTER(F) \
    F(QSharedPointer) \
    F(QWeakPointer) \
    F(QPointer)
```